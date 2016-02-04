# Node Process Object

## Overview

This lesson will cover the `process` global object in Node to get system information and manipulate with the Node instance. 

## Objectives

1. Describe the process objects
2. Describe about process information such as versions, pid, cwd, features, uptime, memoryUsage
3. Describe how to exit the process
4. Describe environment variables
5. Describe standard input and output

## Process Interface

`process` has a lengthy number of properties related to the currently running Node instance and the environment. 

* `process.env`: Environment variables
* `process.pid`: Process ID 
* `process.platform`: Platform, e.g., `darwin`
* `process.cwd()`: Current working directory. Not always the same as `__dirname`.
* `process.version`: Version of node
* `process.versions`: Versions of node, V8, zlib and other Node internal components
* `process.features`: Features of this Node instance, e.g., `debug`p
* `process.arch`: Architecture of this system, e.g., `x64`
* `process.uptime()`: Time this process runs in seconds
* `process.memoryUsage()`: The heap total and used numbers

## Exiting The Process

It also has methods to terminate the process:

* `process.exit(1)`: Exit the current process with errors
* `process.exit(0)`: Exit the current process with no errors
* `process.kill(pid)`: Terminate a process with ID `pid`, e.g., to kill self is `process.kill(process.pid)`

If this was a mouthful of information, don't worry! You can always refer back to this lesson. 

## Environment Variables

One of the important objects in the `process` object is `env`. It stands for environment variables or env vars for short. It's important, because we can pass certain information to our Node process(es) via env vars. Typically information like paths, modes (development or production) or configurations. Also, it's the way to pass sensitive information which we don't want to store in our source code such as usernames/passwords, API keys or information that is specific to that environment.

To access env vars, simply use `process.env.NAME` where `NAME` is capitalized name of the environment variable. For example, `process.env.HOME` will give you a home path if it's set. 

You can set env var in your bash/zsh profile on Macs and Linux, or in Control Panel on Windows. For example, this will append to `PATH` a Rube env var, you can add this line to your bash profile:

```
export PATH="/usr/local/var/rbenv/shims:${PATH}"
```

Another and probably easier way is to prefix your `$ node program.js` command with the variables (or write a shell script with them). For example, we can use `-e` flag to output the `NODE_ENV` variable commonly used to set environment such as development, testing, and production:

```
$ NODE_ENV=production node -e "console.log(process.env.NODE_ENV)"
```

The command will output `production` and terminate. You can run a script instead of using `-e` and pass env vars before the node command. This method is better for variable specific only to your Node program because they won't persist as the profile settings would.

## Standard Input and Output

So how does our Node process communicates with the outside world besides the environment variables? Can we pass some data and get the Node script to output the results that we need? 
Standard input `process.stdin` and output `process.stdout` are the answer. They are streams. 

We'll talk about streams and the input (which is a readable stream) later. For now consider an example in which we output a string:

```js
process.stdout.write('React Quickly \n')
```

The result printing of the string and it is analogous to `console.log()`.


## Resources

1. [Official Process Object Documentation](https://nodejs.org/api/process.html)
1. [The node.js process object video](https://egghead.io/lessons/node-js-the-node-js-process-object)
1. [Environment Variables on Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/ms682653(v=vs.85).aspx)
2. [Node.js Process & Child Process video](https://www.youtube.com/watch?v=9o8B3L0-d9c)


---

<a href='https://learn.co/lessons/node-process' data-visibility='hidden'>View this lesson on Learn.co</a>
