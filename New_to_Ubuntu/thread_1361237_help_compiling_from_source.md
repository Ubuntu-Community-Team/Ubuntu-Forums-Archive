---
title: "help compiling from source"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Extract_Here on 2009-12-21
Okay I know that qbittorrent is in the repository but i want to learn how to compile 
i read some tutorials and i didnt understand them
im not looking for a link to one of them.

i have already configured it but this error occurs when I try to make && install
hayden@hayden-laptop:~/Downloads/qbittorrent-2.0.2$ sudo make && make install
[sudo] password for hayden: 
make: *** No targets specified and no makefile found.  Stop.
 

 thanks in advance

---

### Post by snowpine on 2009-12-21
Didn't like the answers in the first thread, so you started a new one. Cool. :)

---

### Post by Extract_Here on 2009-12-21
are ya here to help? :)

---

### Post by Temposs on 2009-12-21
Do this before running configure again:

```
sudo apt-get build-dep qbittorrent
```

This will install the dependent packages that are needed to build this application. Application source is almost never buildable just by itself. It usually requires having the source for many other libraries. The command above will install all the dependencies automatically. If you were trying to build an app that wasn't in the repositories, you would have to install all the dependencies yourself, manually.

---

### Post by synapsys on 2009-12-21
[http://ubuntuforums.org/showthread.php?t=1361222](http://ubuntuforums.org/showthread.php?t=1361222)

---

### Post by kevdog on 2009-12-21
Did you get your question answered at all?

Did you install the build-essential package as well?

---

### Post by Extract_Here on 2009-12-21
It said the package could not be found

Im not sure what to do

---

### Post by falconindy on 2009-12-21
Quick! Make another thread!

---

