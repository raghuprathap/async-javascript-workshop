# Question 1

Convert the promise version of the multi-file loader over to using async/await

```js
const util = require("util");
const fs = require("fs");
const readFile = util.promisify(fs.readFile);

const files = ["./files/demofile.txt", "./files/demofile.other.txt"];

let promises = files.map(name => readFile(name, { encoding: "utf8" }));
Promise.all(promises).then(values => {
  // <-- Uses .all
  console.log(values);
});
```

# Question 2

Again convert the promise version of the multi-file loader over to using async/await but using a custom async iterator with the following syntax

```js
const fileIterator = files => ({
  [Symbol.asyncIterator]: () => ({
    x: 0,
    next() {
      // TODO
    }
  })
});

const files = ["./files/demofile.txt", "./files/demofile.other.txt"];

(async () => {
  for await (let x of fileIterator(files)) {
    console.log(x);
  }
})();
```
