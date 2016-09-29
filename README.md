#Demo (NodeJS) app for Docker ONBUILD

## How to build this application?

```
$ rm -fr my-node-app-onbuild
```

```
$ git clone https://github.com/sudhaker/my-node-app-onbuild
Cloning into 'my-node-app-onbuild'...
remote: Counting objects: 6, done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 6 (delta 0), reused 6 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), done.
```

```
$ cd my-node-app-onbuild/
```

```
$ docker rmi -f "$(basename $(pwd))"
```

```
$ docker build -t "$(basename $(pwd))" .
Sending build context to Docker daemon 56.83 kB
Step 1 : FROM node:6-onbuild
# Executing 5 build triggers...
Step 1 : ARG NODE_ENV
 ---> Running in dd173f31a43c
Step 1 : ENV NODE_ENV $NODE_ENV
 ---> Running in f9bbaa6eec85
Step 1 : COPY package.json /usr/src/app/
Step 1 : RUN npm install
 ---> Running in ff25c97b46e9
npm info it worked if it ends with ok
npm info using npm@3.10.3
npm info using node@v6.6.0
npm info lifecycle my-node-app@0.0.1~preinstall: my-node-app@0.0.1
npm info linkStuff my-node-app@0.0.1
npm info lifecycle my-node-app@0.0.1~install: my-node-app@0.0.1
npm info lifecycle my-node-app@0.0.1~postinstall: my-node-app@0.0.1
npm info lifecycle my-node-app@0.0.1~prepublish: my-node-app@0.0.1
npm WARN my-node-app@0.0.1 No license field.
npm info ok
Step 1 : COPY . /usr/src/app
 ---> 7231dfec37e1
Removing intermediate container 2b180723665b
Removing intermediate container dd173f31a43c
Removing intermediate container f9bbaa6eec85
Removing intermediate container e36f59ffaf3a
Removing intermediate container ff25c97b46e9
Successfully built 7231dfec37e1
```

```
$ docker run --rm -p 8080:8080 "$(basename $(pwd))"
npm info it worked if it ends with ok
npm info using npm@3.10.3
npm info using node@v6.6.0
npm info lifecycle my-node-app@0.0.1~prestart: my-node-app@0.0.1
npm info lifecycle my-node-app@0.0.1~start: my-node-app@0.0.1

> my-node-app@0.0.1 start /usr/src/app
> node server.js

Server listening on: http://b94d91fb8928:8080
```

**Enjoy!**
