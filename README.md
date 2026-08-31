# Lip Slide Skateboards

Tienda de skateboards estática desarrollada con HTML5, CSS3 y Sass/SCSS. El proyecto permite explorar un catálogo de tablas de skate, conocer al equipo de skaters profesionales, acceder a información general (envíos, pagos, devoluciones) y contactar con la tienda.

---

## Tecnologías utilizadas

- **HTML5** - Estructura y contenido de las páginas.
- **CSS3** - Estilos base compilados desde Sass.
- **Sass/SCSS** - Preprocesador de CSS para organizar y mantener los estilos.
- **Bootstrap 5.3.8** - Framework CSS para el sistema de grilla, navbar responsive y componentes (accordion, toggler). Se carga vía CDN.
- **Font Awesome 6.7.2** - Librería de iconos para redes sociales y navegación. Se carga vía CDN.
- **animate.css 4.1.1** - Librería de animaciones CSS. Se carga vía CDN (utilizada únicamente en la página de equipo).

---
## Puedes ver el proyecto en producción

<https://lipslide-skateboards-store.vercel.app/index.html>
## Instalación

### Prerrequisitos

- [Node.js](https://nodejs.org/) (versión 14 o superior)
- npm (incluido con Node.js)

### Pasos

1. Clonar el repositorio:

```bash
git clone <https://github.com/svitak87/Lipslide-Skateboards>
```

2. Entrar en el directorio del proyecto:

```bash
cd lip-slide-skateboards
```

3. Instalar las dependencias ( Sass):

```bash
npm install
```

Esto instalará Sass como dependencia de desarrollo, que es la única dependencia requerida para compilar los estilos.

---

## Entorno de desarrollo

### Comando principal

```bash
npm run sass
```

Este comando ejecuta Sass en modo **watch** (`--watch`), compilando continuamente los archivos SCSS.

### Detalles de la compilación

| Aspecto               | Detalle                                                        |
| --------------------- | -------------------------------------------------------------- |
| **Archivo de entrada** | `scss/main.scss`                                               |
| **Directorio monitoreado** | `scss/` (todo el directorio y subdirectorios)             |
| **Archivo de salida**  | `styles/styles.css`                                            |
| **Source map**         | `styles/styles.css.map` (generado automáticamente)            |

### Cómo funciona el watch

1. Al ejecutar `npm run sass`, Sass escucha cambios en `scss/main.scss` y todos los archivos parciales que este importa.
2. Cuando se detecta un cambio en cualquier archivo `.scss`, se recompila automáticamente `styles/styles.css`.
3. El proceso continúa hasta que se detenga con `Ctrl + C` en la terminal.

### Flujo de edición

1. Editar cualquier archivo `.scss` dentro del directorio `scss/`.
2. Sass detecta el cambio y recompila `styles/styles.css`.
3. Recargar el navegador (o usar una extensión de live-reload si se configura manualmente) para ver los cambios.

> **Nota:** Sass se ejecuta de forma independiente. No hay servidor de desarrollo integrado. Para previsualizar el sitio, simplemente abrir `index.html` en el navegador o utilizar una extensión como [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) en VS Code.

---

## Flujo de trabajo del desarrollador

1. Clonar el repositorio.
2. Ejecutar `npm install` para instalar las dependencias.
3. Ejecutar `npm run sass` para iniciar la compilación en modo watch.
4. Abrir `index.html` en el navegador (o con Live Server).
5. Editar los archivos `.scss` en `scss/` según la arquitectura definida (ver [Arquitectura Sass](#arquitectura-sass)).
6. Los cambios se reflejan automáticamente en `styles/styles.css`.
7. Recargar el navegador para ver los resultados.

---

## Estructura del proyecto

```text
lip-slide-skateboards/
├── assets/
│   ├── hero/
│   │   ├── hero-image-isection.jpg
│   │   └── blog-img-niños-tea.webp
│   ├── logo/
│   │   └── lipslide-skateboards-logo.png
│   ├── skates/                    (directorio reservado, actualmente vacío)
│   └── team/
│       ├── Andrew-Reynolds.png
│       ├── Bastien-Zalabanzi.png
│       ├── David-Gonzalez.png
│       ├── Geoff-Rowley.png
│       ├── Luan-Oliveira.png
│       └── Tom-Penny.png
├── pages/
│   ├── contact.html               Página de contacto
│   ├── geral-info.html            Información general (envíos, pagos, devoluciones)
│   ├── skates.html                Catálogo de tablas de skate
│   └── team.html                  Equipo de skaters profesionales
├── scss/
│   ├── base/
│   │   ├── _base.scss             Reset, estilos base del body y formularios
│   │   └── _typography.scss       Estilos de tipografía (h1-h3, p, a)
│   ├── layout/
│   │   ├── _blog.scss             Estilos de la sección de blog
│   │   ├── _card.scss             Estilos de las tarjetas de skate (grid, animaciones)
│   │   ├── _footer.scss           Estilos del footer
│   │   ├── _form-contact.scss     Estilos del formulario de contacto
│   │   ├── _hero-image-section.scss  Estilos de la imagen hero principal
│   │   ├── _hero-section-welcome.scss Estilos de la sección de bienvenida
│   │   ├── _navbar.scss           Estilos de la barra de navegación
│   │   └── _team.scss             Estilos de la página de equipo
│   ├── mediaQ/
│   │   └── _mediaQ.scss           Media queries globales (responsive design)
│   ├── utilities/
│   │   ├── _mixins.scss           Mixins reutilizables (typography, skaterCard)
│   │   └── _variables.scss        Variables de colores del proyecto
│   └── main.scss                  Punto de entrada principal de Sass
├── styles/
│   ├── styles.css                 CSS compilado (generado por Sass)
│   └── styles.css.map             Source map (generado por Sass)
├── index.html                     Página principal (home)
├── package.json                   Configuración del proyecto y scripts npm
└── README.md                      Este archivo
```

---

## Arquitectura Sass

### Punto de entrada

El archivo principal es `scss/main.scss`, que importa todos los módulos mediante la sintaxis `@use`:

```scss
@use "./utilities/variables";

@use "./base/base";
@use "./base/typography";

@use "./layout/navbar";
@use "./layout/hero-image-section";
@use "./layout/hero-section-welcome";
@use "./layout/team";
@use "./layout/blog";
@use "./layout/form-contact";

@use "./layout/card";
@use "./layout/footer";

@use "./mediaQ/mediaQ";
```

### Organización de módulos

| Directorio     | Propósito                                                            |
| -------------- | -------------------------------------------------------------------- |
| `utilities/`   | Variables de colores (`_variables.scss`) y mixins reutilizables (`_mixins.scss`). |
| `base/`        | Reset global, estilos del body, formularios (`_base.scss`) y reglas de tipografía (`_typography.scss`). |
| `layout/`      | Estilos de cada componente visual: navbar, hero, blog, cards, equipo, formulario, footer. |
| `mediaQ/`      | Media queries responsive centralizadas en un solo archivo.          |

### Variables disponibles

Definidas en `scss/utilities/_variables.scss`:

| Variable        | Valor     | Uso                          |
| --------------- | --------- | ---------------------------- |
| `$primary`      | `#FFD400` | Amarillo (navbar, acentos)   |
| `$secondary`    | `#E63946` | Rojo (footer, títulos blog)  |
| `$whiter`       | `#ffff`   | Blanco (texto, fondos)       |
| `$background`   | `#0D0D0D` | Fondo principal oscuro       |
| `$surface`      | `#1A1A1A` | Superficies de cards         |
| `$card`         | `#414141` | Bordes de cards              |
| `$text`         | `#1f1f1f` | Texto oscuro                 |
| `$text-muted`   | `#f0f0f0` | Texto claro / inputs         |
| `$border`       | `#3A3A3A` | Bordes generales             |

### Mixins disponibles

Definidos en `scss/utilities/_mixins.scss`:

- **`typography($size, $weight, $spacing, $line-height)`** - Aplica propiedades de tipografía.
- **`skaterCard($width)`** - Estilos base para tarjetas de skaters (ancho, overflow, posición).
- **`skaterCardImage`** - Estilos de imagen para tarjetas de skaters (block, cover, center).

### Cómo agregar o modificar estilos

1. **Nuevo componente visual:** Crear un archivo `_nombre-componente.scss` en `scss/layout/` y agregar `@use "./layout/nombre-componente";` en `main.scss`.
2. **Nueva variable de color:** Agregar en `scss/utilities/_variables.scss`.
3. **Nuevo mixin:** Agregar en `scss/utilities/_mixins.scss`.
4. **Nueva media query:** Agregar en `scss/mediaQ/_mediaQ.scss` siguiendo el patrón existente.
5. **Modificar estilos existentes:** Editar el archivo `_*.scss` correspondiente en el directorio adecuado.

> **Importante:** Todos los archivos parciales deben comenzar con guion bajo (`_`) para que Sass los reconozca como parciales.

---

## Scripts npm disponibles

| Comando         | Descripción                                                                 |
| --------------- | --------------------------------------------------------------------------- |
| `npm run sass`  | Inicia Sass en modo watch. Compila `scss/main.scss` en `styles/styles.css` y monitorea cambios en el directorio `scss/`. |
| `npm test`      | Muestra un mensaje de error indicando que no hay tests configurados.        |


## Solución de problemas

### Sass watcher no se ejecuta

**Síntoma:** Al ejecutar `npm run sass` no ocurre nada o se muestra un error.

**Solución:**
1. Verificar que las dependencias estén instaladas: ejecutar `npm install`.
2. Verificar que el archivo `scss/main.scss` exista.
3. Verificar que Node.js y npm estén correctamente instalados: `node --version` y `npm --version`.

### Cambios en SCSS no aparecen en el CSS

**Síntoma:** Se edita un archivo `.scss` pero `styles/styles.css` no se actualiza.

**Solución:**
1. Verificar que `npm run sass` esté ejecutándose en una terminal abierta.
2. Verificar que el archivo editado esté dentro del directorio `scss/` y sea importado por `main.scss`.
3. Verificar la consola de Sass por errores de sintaxis.
4. Asegurarse de que el archivo tenga extensión `.scss` y no `.css`.

### CSS compilado que no se refleja en el navegador

**Síntoma:** El archivo `styles/styles.css` se actualiza pero el navegador muestra estilos viejos.

**Solución:**
1. Forzar la recarga del navegador con `Ctrl + Shift + R` (o `Cmd + Shift + R` en Mac) para limpiar la caché.
2. Si se usa Live Server, reiniciar el servidor.
3. Verificar que el `<link>` en los HTML apunte correctamente a `./styles/styles.css` o `../styles/styles.css`.

### Rutas incorrectas en los HTML

**Síntoma:** Imágenes, estilos o enlaces no funcionan al abrir las páginas.

**Solución:**
- Las páginas en `pages/` usan rutas relativas con `../` para acceder a la raíz del proyecto.
- Verificar que las rutas en los atributos `src` y `href` sean correctas según la ubicación del archivo HTML.
- La página principal (`index.html`) usa rutas con `./` ya que está en la raíz.

### Errores de npm o Sass

**Síntoma:** Mensajes de error al ejecutar comandos npm o Sass.

**Solución:**
1. Eliminar `node_modules/` y `package-lock.json`, luego ejecutar `npm install` nuevamente.
2. Verificar la versión de Node.js compatibility (versión 14+ recomendada).
3. Si el error menciona un archivo específico, revisar la sintaxis SCSS en ese archivo.

---

## Páginas del sitio

| Página               | Archivo                      | Descripción                                      |
| -------------------- | ---------------------------- | ------------------------------------------------ |
| Inicio               | `index.html`                 | Página principal con hero, bienvenida, blog e info cards. |
| Tablas               | `pages/skates.html`          | Catálogo de tablas de skate con specs y precios. |
| Equipo               | `pages/team.html`            | Skaters profesionales del equipo Lipslide.       |
| Contacto             | `pages/contact.html`         | Formulario de contacto.                          |
| Información general  | `pages/geral-info.html`      | Envíos, medios de pago y políticas de devolución (accordion). |
