# Control de Atrasos — Diseño

> Producto: herramienta de trabajo de Inspectoría (modo "Operar"). Lo marcado **(inferido)** se dedujo del código; confírmalo.

## Dirección
"Libro de registro" institucional: superficies planas, una regla dorada como única firma (borde superior de la cabecera, subrayado de la pestaña activa, tarjeta del reloj), color solo en datos, estado y la acción principal. Identidad de marca **(inferido)**: azul marino + dorado de la insignia del colegio.

## Qué NO se hizo a propósito
Héroe, parallax, barra de progreso, efectos de cursor, coreografía al cargar. Es una herramienta que se usa decenas de veces al día (portería): esos efectos la harían más lenta y menos clara.

## Tokens (en `:root` de `index.html`)
- Color: `--bg --surface --surface-2 --line --line-strong --ink --muted --navy --accent --ok --warn --bad` (+ `-soft`), variante oscura automática (`prefers-color-scheme`) y manual (`data-theme`). Contrastes verificados ≥ 4.5:1 en claro y oscuro.
- Tipografía: títulos y cifras **Barlow Condensed** (600/700), texto **Atkinson Hyperlegible Next** (400/700); ambas autoalojadas en `fonts/` (licencia OFL incluida). El cero tachado es del diseño de la fuente (distingue 0 de O en los RUT).
- Espacio base 4 (`--s1…--s7`), radios `--r-sm/--r/--r-lg`, sombras `--sh-1…3`, capas `--z-*`.
- Movimiento: `--d-fast 120ms`, `--d 180ms`, `--d-slow 240ms`, `--ease-out cubic-bezier(.23,1,.32,1)`. Solo transform/opacity/color; botones `:active` escala .97; hover solo con `(hover:hover) and (pointer:fine)`; `prefers-reduced-motion` lo reduce a ~0.
- Puntos de corte: 860 (tablet), 760 (pestañas con scroll), 640 (móvil: objetivos 44px, modales como hoja inferior), 400.

## Componentes
Cabecera de dos filas (marca + usuario / pestañas subrayadas con scroll en móvil), botones (default/primario/peligro/sm, hover, active, focus, disabled, `aria-busy`), campos con foco y error, teclado numérico del kiosco, tarjeta de resultado, cifras como tipografía (sin tarjetas), tablas (encabezado gris en minúscula, números a la derecha, hover), píldoras de estado, gráficos de barras planos, modales (login, alerta, contraseña, ficha), aviso (toast) con entrada animada, iconos SVG propios (sin emojis).
