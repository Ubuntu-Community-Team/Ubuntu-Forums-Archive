---
title: "how to run jar files on ubuntu vps"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by ubuzion on 2010-07-28
I'm trying to host a game I created on a vps. Only one problem, when I put my run command into my ssh(putty), im trying run jar files, it says permission denied. Is there something i need to install, how do i fix this?

One more thing, how do i set it up for remote connection?

---

### Post by icarus81 on 2010-07-28
Can you give the command

jar files are executed on ubuntu with 
```

java -jar cookie.jar

```

---

### Post by ubuzion on 2010-07-28
@echo off
title Running Test
java -Xmx800m -cp bin;deps/poi.jar;deps/mysql.jar;deps/mina.jar;deps/slf4j.jar;deps/slf4j-nop.jar;deps/jython.jar;log4j-1.2.15.jar; server.Server
pause

this works on windows, this a bat file

---

### Post by ubuzion on 2010-07-28
Come on, someone please help me.
java -Xmx800m -cp  bin;deps/poi.jar;deps/mysql.jar;deps/mina.jar;deps/slf4j.jar;deps/slf4j-nop.jar;deps/jython.jar;log4j-1.2.15.jar;  server.Server

---

### Post by ubuzion on 2010-07-28
bump

---

### Post by ubuzion on 2010-07-28
Omfg, this is the worst forum ever, no help whatsoever

---

