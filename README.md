# Instalación paso a paso de ESLint, Prettier y las guías de estilo de Airbnb

**1.- Tener instalado Visual Studio Code**
Lo podéis encontrar en https://code.visualstudio.com/

**2.- Instalar el plugin ESLint para VSCode**
https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint

**3.- Instalar el pluglin Prettier para VSCode**
https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode

**4.- Instalar para el proyecto (en modo development) los paquetes eslint y premier**

Con YARN:

```console
yarn add -D eslint prettier
```

Con NPM:

```console
npm i -D yarn eslint prettier
```

**5.- Configuración de los estilos de Airbnb**

Con YARN:

```console
yarn add -D eslint-config-airbnb eslint@^#.#.# eslint-plugin-jsx-a11y@^#.#.# eslint-plugin-import@^#.#.# eslint-plugin-react@^#.#.#
```

Con NPM:

```console
npm i -D eslint-config-airbnb eslint@^#.#.# eslint-plugin-jsx-a11y@^#.#.# eslint-plugin-import@^#.#.# eslint-plugin-react@^#.#.#
```

El instalador te hará varias preguntas. Podrás elegir qué versión de eslint quieres instalar. Yo suelo elegir la última estable (antes de las alpha). El resto de las versiones elijo siempre la más moderna.

**6.- Configurar el plugin de Prettier para Eslint.** Con ello conseguimos que ESLint nos muestre los errores de formato cuando a medida que escribimos código.

Con YARN:

```console
yarn add -D eslint-config-prettier eslint-plugin-prettier babel-eslint
```

Con NPM:

```console
npm install -D eslint-config-prettier eslint-plugin-prettier babel-eslint
```

**7.- Archivo de configuración para ESLint.** Creamos un fichero llamado .eslintrc.json con el siguiente contenido.

```json
{
  "extends": ["airbnb", "prettier"],
  "parser": "babel-eslint",
  "plugins": ["prettier"],
  "env": {
    "browser": true,
    "node": true
  },
  "rules": {
    "prettier/prettier": ["error"],
    "no-console": "off"
  }
}
```

Este es el archivo con el que empiezo siempre. Luego, a medida que me hacen falta más funcionalidad, voy ampliando los plugins y las reglas. Por ejemplo, en el archivo de configuración hay una regla (no-console) que le indica a eslint que no marque como error el uso de consolé (por ejemplo consolé.log(x).

En la página de ESLint están podrás encontrar el resto de las reglas
https://eslint.org/docs/rules/

**8.- Archivo de configuración para Prettier**. Creamos el fichero .prettierrc.json con el siguiente contenido.

```json
{
  "printWidth": 100,
  "singleQuote": true
}
```

En este archivo sólo tengo un par de reglas. Suelo poner un ancho de linea de 100 caracteres y utilizo comillas simples.

En la página oficial de Prettier encontrarás el resto de las opciones.
https://prettier.io/docs/en/options.html

... y esto es todo.

La diferencia la podéis comprobar en estas dos imágenes. En la primera aparece un fichero index.js en VS Code dentro de un proyecto sin ESLint, Prettier ni las reglas de Airbnb instaladas.

![alt text](https://rober.dev/content/images/2019/05/Screenshot-2019-05-31-at-08.37.57-1.png 'Proyecto sin librerías ESLint, Prettier y guías de estilo Airbnb instaladas')

... en el segundo están instaladas.

![alt text](https://rober.dev/content/images/2019/05/Screenshot-2019-05-31-at-08.38.19.png 'Proyecto sin librerías ESLint, Prettier y guías de estilo Airbnb instaladas')
