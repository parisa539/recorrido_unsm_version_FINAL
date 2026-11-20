# Recorrido de bienvenida UNSM con realidad aumentada

## 1. La idea en una frase
Un **folleto de bienvenida** con el mapa de la Ciudad Universitaria. El ingresante lo escanea con su celular y **los edificios salen en 3D sobre el mapa**. Al tocar un edificio o un pin, ve qué facultad o servicio es, y puede seguir un **recorrido guiado** paso a paso.

## 2. ¿Qué problema resuelve?
Los ingresantes no conocen el campus: no saben dónde está su facultad, el comedor, el centro médico o por qué puerta entrar. Un mapa en papel es difícil de entender. En 3D se entiende al toque, y funciona **sin instalar ninguna app**.

## 3. ¿Qué se muestra?
- Los 9 bloques de facultades (A a I) en 3D, con su forma real según el croquis oficial.
- Edificios estilo maqueta (paredes claras y techos de teja), árboles, piscina con agua, el monumento y la portada de la Puerta 1, inspirados en la maqueta física y la vista satelital del campus.
- Pines de servicios: Comedor, Cafetín 1, Cafetería saludable, Piscina, Campo deportivo, Losas deportivas, Centro Médico, Auditorio de Videoconferencias, Monumento Carlos Vidaurre, Puerta 1 y Puerta 2.
- Una ficha con información al tocar cada lugar.
- Un **recorrido guiado** de 20 pasos, desde la Puerta 1 hasta la Puerta 2.
- **📍 ¿Cómo llego?**: eliges tu facultad o un lugar y, desde la Puerta 1 o la Puerta 2, aparece una **ruta azul** por las pistas del campus con un **personaje caminando** hasta el destino. También se puede pedir desde la ficha de cada lugar (botón "Cómo llegar"). Debajo aparece la ruta **paso a paso**: *Sales desde…*, *Pasas por…* y *¡Llegaste a tu destino!*, con la foto de cada lugar, y se marca el paso donde va el personaje. Con el botón **▼** se oculta la lista (la ruta azul sigue en el mapa) y con **▲** vuelve a aparecer.
- **📷 Fotos reales** en la ficha de cada lugar (si se suben al repositorio).
- Un botón **❄️ Congelar** para tocar todo tranquilo sin mover el celular.
- **Funciona con el folleto y también con el croquis oficial**, en papel o en una pantalla.
- **📤 Subir imagen del croquis (sin papel):** con el botón *📤 Subir imagen* (arriba a la derecha, cuando ya estás en la cámara), eliges una foto o captura del croquis (o del folleto) y la app la escanea en lugar de la cámara. También hay un botón para usar el **croquis oficial** directamente. Con *📷 Usar cámara* se vuelve a la cámara.

## 4. Herramientas (todas gratuitas, en lugar de Adobe Aero, que fue descontinuado)
| Para qué | Herramienta |
|---|---|
| Reconocer el folleto con la cámara | MindAR (código abierto) |
| Maqueta 3D, pines y animaciones | A-Frame (basado en Three.js) |
| Publicar la página con HTTPS | GitHub Pages |
| Abrir la página | Link o código QR |

## 5. ¿Cómo funciona por dentro?
1. El folleto se convierte en una "huella" (`targets.mind`) con miles de puntos de referencia.
2. Al apuntar la cámara, MindAR busca esos puntos en el video y calcula dónde está el folleto y cómo está inclinado.
3. A-Frame dibuja la maqueta 3D encima, usando el folleto como piso.
4. Un estabilizador evita que la maqueta tiemble, y se corrigió el ángulo de cámara de MindAR (de 45° a 65°) para que coincida con la cámara real del celular.

## 6. Datos utilizados (reales)
- Ubicación de bloques, servicios y puertas: **croquis oficial de la Ciudad Universitaria UNSM**.
- Estilo de los edificios y lugares extra (monumento, cafetines): maqueta física del campus y vista satelital (usadas solo como referencia; el mapa es un dibujo propio).
- Facultades y escuelas: información pública de la UNSM.
- Los horarios se pueden agregar en `index.html` (sección DATOS, campo `horario`).

## 7. Cómo agregar fotos reales
Sube al repositorio una foto por lugar con **este nombre exacto** (en minúsculas, formato .jpg). La ficha la mostrará sola:

| Lugar | Nombre del archivo |
|---|---|
| Bloque A (FISI) … Bloque I (FDCP) | `foto-a.jpg`, `foto-b.jpg`, `foto-c.jpg`, `foto-d.jpg`, `foto-e.jpg`, `foto-f.jpg`, `foto-g.jpg`, `foto-h.jpg`, `foto-i.jpg` |
| Comedor | `foto-comedor.jpg` |
| Cafetín 1 | `foto-cafetin.jpg` |
| Cafetería saludable | `foto-cafeteria.jpg` |
| Centro Médico | `foto-medico.jpg` |
| Auditorio | `foto-auditorio.jpg` |
| Piscina | `foto-piscina.jpg` |
| Losas deportivas | `foto-losas.jpg` |
| Campo deportivo | `foto-campo.jpg` |
| Monumento | `foto-monumento.jpg` |
| Puerta 1 / Puerta 2 | `foto-puerta1.jpg`, `foto-puerta2.jpg` |

Usa fotos tomadas por ti, en horizontal y livianas (menos de 300 KB cada una) para que carguen rápido con datos móviles.

**Fotos incluidas ahora:** Puerta 1, Puerta 2, FISI (A), FEH (D), FMH (B), FDCP (I), Comedor, Centro Médico, Monumento y FCE (H). Al tocar cualquier foto (en la ficha o en los pasos de la ruta) se abre en grande.
Las fotos de FEH y FMH son de Manuel Rojas en Google Maps y llevan su crédito en la ficha (campo `credito` en `index.html`). Lo ideal es reemplazarlas por fotos propias cuando se pueda.

## 8. Cómo publicarlo
1. Crear un repositorio público en GitHub (por ejemplo `recorrido-unsm`).
2. Subir los archivos: `index.html`, `targets.mind`, `mindar-image-aframe.prod.js`, `escudo.png`.
3. Settings → Pages → rama `main`, carpeta `/ (root)` → Save.
4. Abrir `https://TU-USUARIO.github.io/recorrido-unsm/` en Chrome (Android) o Safari (iPhone).

## 9. Consejos para la demo
- Imprime `folleto-bienvenida-A4.pdf` en papel mate (que no brille).
- Pon el folleto sobre la mesa y sostén el celular **en horizontal** para que entre todo el mapa.
- Muévete despacio. Para mostrar las fichas, toca **❄️ Congelar** y luego toca los edificios.
- Usa **🧭 Recorrido** para mostrar el paso a paso.

## 10. Guion corto para exponer (2 minutos)
1. "Cuando ingresamos a la UNSM no sabíamos dónde quedaba nada."
2. "Hicimos un folleto de bienvenida con realidad aumentada, que funciona desde el navegador, sin instalar apps."
3. *(Escanear)* "Al apuntar con el celular, los edificios salen en 3D sobre el mapa."
4. *(Tocar un bloque)* "Si toco un edificio, veo qué facultad es y qué escuelas tiene."
5. *(¿Cómo llego?)* "Si soy ingresante de Economía, elijo FCE y me muestra el camino desde la puerta: salgo por la Puerta 1, paso por el Monumento, el Cafetín y FICA, y llego a mi facultad. Cada paso tiene su foto."
6. *(Recorrido)* "Y con el recorrido guiado, el ingresante conoce todo el campus paso a paso."
7. "Usamos herramientas gratuitas: MindAR y A-Frame, como alternativa a Adobe Aero, que fue descontinuado."

## 11. Novedades de la versión 11
- **Comenzar** ya responde al primer toque. Mientras se abre la cámara aparece "Abriendo la cámara…".
- **¿Desde dónde sales?** En ¿Cómo llego? puedes salir de 📍 Mi ubicación, 🚪 Puerta 1, 🚪 Puerta 2 u **Otro lugar** (cualquier facultad, el comedor, etc.).
- **📍 Dónde estoy (GPS, como Google Maps).** El punto rojo eres tú. Si eliges "Mi ubicación" como inicio:
  - la ruta empieza donde estás y se marca el paso en el que vas mientras caminas;
  - los metros y minutos que faltan se actualizan;
  - si te sales del camino, la ruta se recalcula;
  - al llegar te avisa con "¡Llegaste!".
- Para caminar sin apuntar al folleto: **📤 Subir imagen → Usar el croquis oficial**, y luego activa tu ubicación.
- Si tu punto sale corrido, toca **"¿Tu punto sale mal? Ajústalo"** y elige junto a qué lugar estás.
- Fuera del campus, la app avisa que estás lejos y te deja elegir otro punto de inicio.
- **Para la exposición en clase (fuera del campus):** abre el link agregando `&modo=croquis&gpsdemo=1`. Así se simula una persona que camina de la Puerta 1 al Comedor:
  `https://parisa539.github.io/recorrido_unsm/?v=11&modo=croquis&gpsdemo=1`
