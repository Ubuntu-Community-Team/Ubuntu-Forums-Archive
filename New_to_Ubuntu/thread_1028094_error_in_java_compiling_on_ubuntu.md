---
title: "error in java compiling on ubuntu"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by m.balakrishnan on 2009-01-02
javac bala.java

javac: file not found: bala.java
Usage: javac <options> <source files>
use -help for a list of possible options

[COLOR="Red"]how to clear this error?[/COLOR]

---

### Post by kavon89 on 2009-01-02
Are you sure your Terminal is in the correct directory and the filename is exact (case sensitive)?

---

### Post by m.balakrishnan on 2009-01-02
ya my terminal is accesories--->terminal. then 
what will i do?

---

### Post by m.balakrishnan on 2009-01-02
this is my program

import.java.io.*;
class bala
{
public static void main(String args[])throws IOException
{
System.out.println("krishna");
}
}
 
file name is bala.

---

### Post by m.balakrishnan on 2009-01-02
but my java language installed in Application--->Internet------>sun java 6 web start.

---

### Post by kyeh on 2009-01-02
firstly, use the 'ls' command and see if your file is there.

if not, use the 'cd' command to change to your directory where your file is.

for example, if your file was in ~/first/second, type cd first/second

also, the source file should end in .java , i'm not too sure about this... but usually i do that

---

### Post by carml on 2009-01-02
It's the first program you try to write?

---

### Post by m.balakrishnan on 2009-01-02
ya it is first time in ubuntu.

---

### Post by m.balakrishnan on 2009-01-02
i know java but i don't make any program through ubuntu. So tell how to compile java program using terminal on ubuntu.

---

### Post by kyeh on 2009-01-02
Where did you save the source file?

---

### Post by carml on 2009-01-02
I think you need to install a package similar to JDE(Java development environment);some time ago I coded a bit with Java on a Windows machine,and I had to install a development environment,a Java Virtual Machine serves only to run in the browser the already written programs.
I hope this suggestion may help you. :)

---

### Post by m.balakrishnan on 2009-01-02
in desktop. file name:bala.java

---

### Post by m.balakrishnan on 2009-01-02
> **carml said:**
> I think you need to install a package similar to JDE(Java development environment);some time ago I coded a bit with Java on a Windows machine,and I had to install a development environment,a Java Virtual Machine serves only to run in the browser the already written programs.
I hope this suggestion may help you. :)

**[COLOR="Red"]How to find that packages are in my ubuntu system?[/COLOR]**

---

### Post by m.balakrishnan on 2009-01-02
> **kyeh said:**
> Where did you save the source file?

in desktop

---

### Post by carml on 2009-01-02
Look for the correct package in System->Synaptic package manager,then there search the more adeguate package.

---

### Post by m.balakrishnan on 2009-01-02
> **carml said:**
> Look for the correct package in System->Synaptic package manager,then there search the more adeguate package.

but that package is not in my system. how do get that packages?

---

### Post by carml on 2009-01-02
Select the little square you see in System->Synaptic package manager,you have to simply right click the square and select mark for installation.:P

---

### Post by m.balakrishnan on 2009-01-02
> **carml said:**
> Select the little square you see in System->Synaptic package manager,you have to simply right click the square and select mark for installation.:P

icedtea-java7-jdk which package is in system. but i have installed sun java 6 web start. 

if i will installe that icedtea-java7-jdk package, will it match?

is it possible?

---

### Post by kyeh on 2009-01-02
try this,

open terminal

```

cd Desktop
javac YOUR_FILE

```

---

### Post by carml on 2009-01-02
Yes it may match,IMHO :).

---

### Post by kavon89 on 2009-01-02
First off, your code never throws an IOException.

```
public class bala {
public static void main(String args[]) {
System.out.println("krishna");
    }
}
```

Use that instead for a correct "hello world" program.

Read this link for more detailed instructions on how to compile and then turn the .class files into an executable .jar:

[http://java.sun.com/docs/books/tutorial/rmi/compiling.html](http://java.sun.com/docs/books/tutorial/rmi/compiling.html)

Also, open up the Synaptic Package Manager (System -> Administration) and search "sun-java6". a whole bunch of packages will come up, make sure you mark the following for installation (if the box is green you already have it installed)

sun-java6-jdk
sun-java6-jre

If you have more, like sun-java6-bin installed thats fine. You need at least those packages to get started.

---

