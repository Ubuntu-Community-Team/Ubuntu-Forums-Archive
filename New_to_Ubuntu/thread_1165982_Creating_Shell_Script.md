---
title: "Creating Shell Script"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by poscomp on 2009-05-21
I come from a DOS environment where I used .bat files all the time. I am told I can do the same thing in Ubuntu Linux with shell scripts. How would I create a simple shell script like this bat file:

cd downloads
gedit
cd ..
exit


Can someone help me?

---

### Post by kpkeerthi on 2009-05-21
Just put those lines in a file, say **myscript** and then run it like this ```
bash myscript
```
* This is the simplest possible way I could think of. For more info see [Bash Scripting]("http://www.google.com/search?q=bash+scripting").

---

### Post by benj1 on 2009-05-21
```
#! /bin/bash

cd /full/path/to/downloads
gedit
cd ..
```
in a terminal change to the directory and type
```
chmod +x nameofscript
```
to make it executable
then ```
./nameofscript
``` to run

have a look at the [advanced bash scripting guide]("http://www.tldp.org/guides.html")
its a good guide for bash scripting

---

### Post by darthmob on 2009-05-21
what do you want to achieve with that script?

---

