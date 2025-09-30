
# Teachable Machine + micro:bit

## Descripción

Esta aplicación web utiliza inteligencia artificial para detectar parámetros faciales en tiempo real usando la cámara del dispositivo. Los datos detectados se envían por Bluetooth a una placa micro:bit, permitiendo controlar proyectos físicos con gestos y expresiones.

## Funcionalidades principales

- **Detección facial en tiempo real:** Utiliza TensorFlow.js y el modelo Face Landmarks Detection para extraer puntos clave del rostro.
- **Visualización:** Muestra los puntos detectados sobre el video, diferenciando entre cámara frontal y posterior, y adaptándose a PC y móvil.
- **Parámetros faciales:** Calcula y muestra en pantalla 12 parámetros en español:
  - Ubicación X, Ubicación Y, Distancia (Z)
  - Giro Yaw, Inclinación Pitch, Rotación Roll
  - Boca (apertura), Ojo Izquierdo, Ojo Derecho, Sonrisa
  - Visible (rostro detectado), Estado (Sí/No)
- **Bluetooth micro:bit:** Permite conectar y desconectar la micro:bit fácilmente. Envía los parámetros faciales en tiempo real.
- **Controles adaptativos:** Botones para iniciar/detener la detección y cambiar de cámara, con diseño responsivo para móvil y escritorio.
- **Feedback:** Muestra los últimos comandos enviados a la micro:bit.

## Cómo funciona el envío de datos

Cada vez que se detecta el rostro, la app envía una cadena de números a la micro:bit, con el siguiente formato:

```
XXYYZZYYPPMMLELRRSV
```

Donde cada grupo representa:

- `XX`: Ubicación X (2 dígitos, 00-99)
- `YY`: Ubicación Y (2 dígitos, 00-99)
- `ZZ`: Distancia (2 dígitos, 00-99)
- `YY`: Giro Yaw (2 dígitos, 00-99)
- `PP`: Inclinación Pitch (2 dígitos, 00-99)
- `MM`: Boca (2 dígitos, 00-99)
- `LE`: Ojo Izquierdo (2 dígitos, 00-99)
- `LR`: Ojo Derecho (2 dígitos, 00-99)
- `R`: Rotación Roll (1 dígito, 0-9)
- `S`: Sonrisa (1 dígito, 0-9)
- `V`: Visible (1 dígito, 0=No detectado, 1=Detectado)

Ejemplo de cadena enviada:
```
23045550301234011
```
Cada valor está normalizado entre 0 y 99 (o 0 y 9 para los últimos parámetros).

## Requisitos

- Navegador compatible con Web Bluetooth (Chrome recomendado).
- micro:bit con Bluetooth activado y el servicio UART disponible.
- Permitir acceso a la cámara.

## Uso

1. Abre la página web en tu navegador.
2. Permite el acceso a la cámara.
3. Haz clic en "Iniciar Detección".
4. Conecta la micro:bit con el botón correspondiente.
5. Observa los parámetros y los puntos verdes sobre el video.
6. Cambia de cámara si lo necesitas (en móvil).
7. Los datos se envían automáticamente a la micro:bit mientras el rostro esté detectado.

## Personalización

- Puedes modificar el código para cambiar la frecuencia de envío, los parámetros calculados o el diseño visual.
- El código es abierto y editable.

