

To start we have to config the tsconfig.json
```console
tsc --init
```

then open and modify it :
```json
"outDir": "./build",
"rootDir": "./src"
```

create the two directory `build` & `src` and create a `index.ts`
```console
mkdir build && mkdir src
touch src/index.ts
```

open the `index.ts` file and write some Typescript code then run :
```console
tsc src/index.ts
```

And It should create a `index.js` into the `build` directory

To automate the process of transpilation. 
We have to install `nodemon` & `concurrently`

run :
```console
npm -init y #to create the package.json
npm install --save nodemon concurrently # to install the two npm modules
```

then open the `package.json` and add the scripts below :
```json
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "start:build": "tsc -w",
  "start:run": "nodemon build/index.js",
  "start": "concurrently npm:start:*"
}
```

then when you run `npm start` it will concurrently `nodemon` & `tsc -w`
After each save of the typescript code, the code will be transpiled into javascript & nodemon will relaunch the sever. 

