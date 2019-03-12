<h1 align="center">
  <br>
  <a href="#"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/React-icon.svg/2000px-React-icon.svg.png" alt="react-helloworld" width="100"></a>
  <br>
  React Hello World
  <br>
</h1>

**1. Create package.json file:**

  ```
  npm init
  ```


**2. Install app dependencies:**

  ```
  npm install --save react react-dom
  ```


**3. Install app development dependencies:**

  - For compiling jsx or es6 to browser supporting plain javascript:

   ```
   npm install --save-dev babel-cli babel-loader babel-preset-es2015 babel-preset-react
   ```

  - For hot reloading of localhost server in browser:

    ```
    npm install --save-dev webpack webpack-cli webpack-dev-server
    ```

**4. Setup index.html:**

  - Create index.html and add following code:

  ```
  <!DOCTYPE html>
  <html>
    <head>
      <title>React App Setup</title>
    </head>
    <body>
      <div id='app'></div>
      <script src='./app.js'></script>
    </body>
  </html>
  ```

**5. Setup react app in app.js:**

  - Create app.js and add following code:

  ```
  import React from 'react'
  import ReactDOM from 'react-dom';
  import HelloWorld from './components/HelloWorld';
  ReactDOM.render(<HelloWorld />, document.getElementById('app'));
  ```

  - Create 'HelloWorld' component and add following code:

  ```
  import React from 'react';
  class HelloWorld extends React.Component {
    render() {
      return (
        <div>
          <h1>Hello World</h1>
          <p>Welcome to my world dude</p>
        </div>
      );
    }
  }
  export default HelloWorld;
  ```

**6. Setup babel to transform our JSX to regular javascript:**

  - Create a .babelrc file and following scripts:

  ```
  { "presets": ["react", "es2015"] }
  ```

**7. Setup webpack by configuring it:**

  - Create a webpack.config.js file and add following code:

  ```
  var webpack = require('webpack');
  module.exports = {
    entry: {
      app: './app.js'
    },
    mode: 'development',
    output: {
      path: __dirname + '/dist',
      publicPath: '/',
      filename: 'app.js'
    },
    module: {
      rules: [
        {
          test: /\.jsx?$/,
          loader: 'babel-loader',
          exclude: /node_modules/,
          query: {
            cacheDirectory: true,
            presets: ['react', 'es2015']
          }
        }
      ]
    }
  }
  ```

**8. Setup npm scripts by adding following code:**

  ```
  "scripts": {
    "start": "webpack-dev-server",
    "test": "echo \"Error: no test specified\" && exit 1"
  }
  ```

**9. start react app:**

  npm start
