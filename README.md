# Kánaritech Sim · Drive Lab

Simulador web de práctica con el modelo MK_28 de Kánaritech 9499, construido con Three.js y JavaScript.

## Publicar con GitHub Pages

En **Settings → Pages → Build and deployment**, selecciona **Deploy from a branch**, rama **main**, carpeta **/docs**, y pulsa **Save**.

La dirección esperada es `https://osvillat-alt.github.io/KanaritechSim/`. Espera a que GitHub confirme el despliegue antes de abrirla. La carpeta `docs/` incluye el sitio compilado y el modelo 3D, con rutas relativas para que funcione bajo el nombre del repositorio o con un dominio propio. No requiere el acceso de ChatGPT de la publicación original.

## Controles

Pulsa **Iniciar práctica**. WASD mueve el robot respecto a la cancha; Q/E gira el chasis; Shift reduce la velocidad; I activa el intake; B o Espacio activa el shooter; Y activa el modo alimentación; T activa ayuda de apuntado al aro azul; J/L mueve la torreta; ↑/↓ ajusta el ángulo; P pausa; R reinicia. También hay soporte para mando Xbox, controles táctiles de desplazamiento y WebXR experimental.

El modelo 3D requiere WebGL. Se ofrece una cancha 2D de respaldo cuando no está disponible. Para entrar a VR, utiliza un navegador WebXR compatible, como Meta Quest Browser, desde HTTPS. El modo VR aún requiere validación en un Quest real.

## Desarrollo local

Requiere Node.js y npm.

```sh
npm ci
npm run check
npm run build
```

Sirve `docs/` mediante un servidor estático. Tras modificar el código, ejecuta la compilación y sube también los cambios de `docs/`. GitHub Pages publica directamente esa carpeta.

## Alcance y fidelidad

Conducción holonómica con referencias del código oficial: 5.30 m/s y 270°/s. El simulador no ejecuta Java/WPILib ni emula controladores de motor. Aceleración, fricción, velocidad de salida, capacidad, colisiones y puntuación son aproximaciones de práctica. La cancha no reproduce el reglamento de una temporada. T, J/L, I y LB son controles añadidos de práctica; los movimientos visuales y pivotes necesitan calibración con el robot real.

El GLB optimizado ocupa aproximadamente 4.2 MB, con 674,891 triángulos y 20 primitivas. Se conservaron las posiciones del ensamble, colores y grupos animables; los pivotes se documentan en `docs/assets/asset-map.json`. El original de Onshape y el código Java del robot no se incluyen en este repositorio.

Los scripts `scripts/prepare-robot.py` y `scripts/optimize-robot.mjs` permiten reproducir la preparación del modelo si se proporciona el GLB original; el primero necesita Python con NumPy.

## Validación

Se comprobaron normalización de velocidad diagonal, límites de cancha y ángulo de disparo. Se validó la decodificación del modelo Meshopt y cuatro posiciones de ruedas distintas. En el navegador remoto sin WebGL se probaron desplazamiento, recolección, disparo y aciertos mediante el respaldo 2D. La visualización 3D y el modo VR necesitan validarse en el equipo/visor de destino.
