# Nodejs-learning
Basic nodejs 

## What is Noedjs
Node.js is a runtime for built on top of Chrome's V8. It allows you to develop apps in JavaScript outside of the browser. It's single threaded non blocking and asynchronous. This is acheived by the use of an event loop at the core of Node.js. 

Node.js can be used to build different types of applications such as command line application, web application, real-time chat application, REST API server etc. However, it is mainly used to build network programs like web servers, similar to PHP, Java, or ASP.NET form wiki.


## Running a file :
` node index.js`

## Gloabl :
Node.js global objects are global in nature and they are available in all modules. We do not need to include these objects in our application, rather we can use them directly.

### Getting directory name:
`console.log( __dirname );` 

### File name 
`console.log(__filename);

PS D:\nodejs-learning\webserver> node .\index.js
D:\nodejs-learning\webserver
D:\nodejs-learning\webserver\index.js`

## Process object :

exe path
` process.execPath
'C:\\Program Files\\nodejs\\node.exe'`

### Getting process id 

`process.pid
20000`

There are more global objects get here  
https://nodejs.org/api/globals.html


## Module:
A module is a reusable chunk of code that has its own context

## Built-In Module :
node have some built-in modules https://www.w3schools.com/nodejs/ref_modules.asp

## Include Module 
To include a module, use the **require()** function with the name of the module:
`const http = require('http')`

## Creating a Module :
my-module.js
```
const action = () => {
    console.log("action function is excuting")
}
module.exports = action
```
index.js
```
const action = require('./my-module');
action()
```
o/p
> action function is excuting

## NPM:
npm is a package manager for the JavaScript programming language maintained by npm, Inc. npm is the default package manager for the JavaScript runtime environment Node.js. from wiki
## Installing packages:

### install pakage gloablly
```
npm install -g nodemon
npm test - runs the test script in your package.json
npm uninstall - will uninstall a give package
```
npm init for can be used to set up a new or existing npm package

## Packages.json
The package. json file is the heart of any Node project. It records important metadata about a project which is required before publishing to NPM, and also defines functional attributes of a project that npm uses to install dependencies, run scripts, and identify the entry point to our package


## Error handling :
https://lucymarmitchell.medium.com/using-then-catch-finally-to-handle-errors-in-javascript-promises-6de92bce3afc

https://nodejs.dev/learn/error-handling-in-nodejs

### Async Errors:
wait for promises to return
```
try {
    const result = await asyncAction()
  } catch (e) {
    // handle error
  }
  ```

### Sync Errors:
```
try {
    const result = syncAction()
  } catch (e) {
    // handle error
  }
```

### Http module:
```
const http = require('http')
//create server objects
http.createServer(function (req,res){
    res.writeHead(200,{'Content-type':'text/html'})
    res.write('<h1>hello world</h1>');
    res.end()
    
}).listen(8080);

```
## Filesystem Module:
## File read:
```
var http = require('http')
var fs = require('fs')

http.createServer(function (req,res){
    fs.readFile('xss.html',function(err,data){
        res.writeHead(200,{'Content-type':'text/html'});
        res.write(data);
        res.end();
    })
}).listen(80);
```
### File read with error :
```
const fs = require('fs');
fs.readFile('./write.txt',(err,data) =>{
    if (err){
        console.log(err);
    }
    console.log(data.toString())
});
console.log("last line")
```

### File write:
```
var fs = require('fs')
var content="This is content will be saved to one file "
fs.writeFile('write.txt',content,function(err){
    if (err) throw err;
    console.log("saved..!")
});
```

### File append:
```
var fs = require('fs');
fs.appendFile('write.txt','its new content to save',function(err){
    if (err) throw err;
    console.log("append...!")
})
```

### File delete:
```
var fs = require('fs')
fs.unlink('write.txt',function(err){
    if (err) throw err;
    console.log("File deleted..!")
})
```

## Express framework:
### Express:
Express.js, or simply Express, is a back end web application framework for Node.js, released as free and open-source software under the MIT License. It is designed for building web applications and APIs. It has been called the de facto standard server framework for Node.js from wiki

### Installation 
`npm install express `

it will automatically update package.json

### Express : Listening
```
const express = require('express');
const app = express();
//server listen
app.listen(3000);
//sending response 
app.get('/',(req,res)=> {
    res.send("Hello world")
})
```

### Routing and HTML

```
const express = require('express');
const app = express();
//server listen
app.listen(3000);
//sending response 
app.get('/',(req,res)=> {
    //res.send("Hello world")
    res.sendFile('./pages/index.html',{root:__dirname});
});
app.get('/about',(req,res)=>{
    res.sendFile('./pages/about.html',{root:__dirname})
});
```


## Middleware:

A middleware is basically a function that will the receive the Request and Response objects, just like your route Handlers do. As a third argument you have another function which you should call once your middleware code completed.

```
//Middleware 
app.use((req,res,next) => {
    console.log("Hostname:",req.hostname);
    console.log("Method:",req.method);
    next();
});
```
https://selvaganesh93.medium.com/how-node-js-middleware-works-d8e02a936113


## Mongoose :
https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/mongoose



## Tutorials:
https://www.w3schools.com/nodejs/
https://www.tutorialspoint.com/nodejs/index.htm

## Video-Creating a Blog:
https://www.youtube.com/watch?v=yXEesONd_54&ab_channel=TheNetNinja

## NodeJS cheat sheet
https://overapi.com/nodejs

## Javascript cheat sheet
https://websitesetup.org/javascript-cheat-sheet/

https://htmlcheatsheet.com/js/


