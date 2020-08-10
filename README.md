# React with Jest and Enzyme

## How to add Jest and Enzyme to react project (create-react-app)

1. Create react project using create-react-app

   ```javascript
   npx create-react-app my-app
   ```

2. Add `enzyme`, `jest-enzyme`, and `enyme-adapter-react-16` to the project as dev dependencies

   ```javascript
   yarn add enzyme jest-enzyme enzyme-adapter-react-16 -d
   ```

3. Add `jsconfig.json` to the root folder with `jest` type acquisition for jest intellisense/code completion.

   ```json
   {
     "typeAcquisition": {
       "include": ["jest"]
     }
   }
   ```

4. Add `data-test` attribute for testing the component if necessary

   ```html
   <div className="App" data-test="component-app">
     <h1>Hello world!</h1>
   </div>
   ```

5. Remove the `data-test' attribute from production

   1. `yarn add babel-plugin-react-remove-properties -d`

   1. `yarn run eject`

   1. Update babel config in `package.config`

      ```json
      {
        "babel": {
          // this configuration removes the data-test attribute
          "env": {
            "production": {
              "plugins": [
                [
                  "react-remove-properties",
                  {
                    "properties": ["data-test"]
                  }
                ]
              ]
            }
          },
          "presets": ["react-app"]
        }
      }
      ```

   1. Create production build

      ```javascript
      yarn run build
      yarn global add serve
      server -s build
      ```

   1. Now inspect the page and check, `data-test` attributes are gone!

---
