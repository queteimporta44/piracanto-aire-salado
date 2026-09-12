# Piracanto — rediseño

Rediseño de la tienda [piracanto.com](https://piracanto.com), una marca colombiana de
resortwear. Una sola página estática, sin dependencias ni proceso de build: se abre
`index.html` en cualquier navegador y funciona.

La dirección visual toma prestada la paleta y la tipografía de **Johanna Ortiz** y
**Cult Gaia**, medidas sobre sus sitios reales en lugar de aproximadas a ojo.

## Paleta

| Token | Valor | Origen |
| --- | --- | --- |
| `--arena` | `#F5F1EC` | fondo de Johanna Ortiz |
| `--concha` | `#FFFEF8` | superficies de Cult Gaia |
| `--tinta` | `#222222` | texto de Johanna Ortiz |
| `--piedra` | `#393939` | texto de Cult Gaia |
| `--abismo` | `#1A1714` | negro cálido para el matte de imagen |
| `--caoba` | `#784C4A` | color exacto del logotipo de Piracanto |

Tipografías: **Amiri** para títulos y **Libre Franklin** para el resto, las mismas dos
que usa Johanna Ortiz. El grid replica los valores literales de Cult Gaia: dos columnas
en móvil con `gap` de 8px.

## El problema que resuelve

El catálogo mezcla proporciones de imagen:

| Proporción | Imágenes |
| --- | --- |
| 2:3 vertical | 404 |
| 3:4 vertical | 2 |
| 3:2 horizontal | 13 |

Forzarlas todas al mismo marco con `object-fit: cover` recorta las horizontales por
cabeza y pies. Aquí cada foto vive en una *vitrina* que mantiene la proporción y la
deja entrar entera con `object-fit: contain`; el aire sobrante es el negro cálido de
la marca, que se lee como paspartú y no como error.

La portada va un paso más allá y cambia de proporción según el dispositivo —2:3 en
móvil, 3:2 en escritorio, vía `<picture>`— de modo que en ambos casos el marco coincide
con la proporción nativa de la foto y no sobra nada.

## Responsive

| | Móvil | ≥700px | ≥1100px | ≥1500px |
| --- | --- | --- | --- | --- |
| Grid | 2 col | 3 col | 4 col | 5 col |
| Navegación | cajón lateral | cajón | menú horizontal | menú |
| Editorial | apilado | apilado | dos columnas | dos columnas |
| Ficha | hoja inferior | hoja inferior | diálogo centrado | diálogo centrado |
| Pie | 2 col | 4 col | 4 col | 4 col |

## Contenido

Los 30 productos son los reales de la tienda, en su mismo orden, con sus precios en
pesos colombianos, sus variantes de color y talla, sus tres fotos de galería y las
descripciones que escribió la marca. Los recuentos por categoría —Mujer 19, Hombre 10,
Unisex 2, Vestidos 4, Sets 5— salen calculados del catálogo y cuadran con la tienda.
Unisex es un subconjunto de Hombre, que es lo que hace que 19 + 10 + 2 den 31 para 30
productos.

## Estructura

```
index.html    la página entera: markup, estilos y comportamiento
img/          logotipo y 92 fotos de producto y campaña
```

Las imágenes y el logotipo pertenecen a Piracanto y se incluyen únicamente a efectos
de esta propuesta de rediseño.
