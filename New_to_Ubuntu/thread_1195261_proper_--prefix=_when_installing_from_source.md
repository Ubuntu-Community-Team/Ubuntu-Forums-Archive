---
title: "proper --prefix= when installing from source"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by stimpak on 2009-06-23
ehm i dont know if its really for beginners, but its pretty basic. If needed a mod should feel free to move it where it needs.


Whats the proper prefix flag you what you need to declare when you're ./configure -ing  a program for an installation from the source? 


In other words, how you're complete this ? ./configure --prefix=???

---

### Post by KIAaze on 2009-06-23
```
./configure --prefix=PREFIX
```
This will install the binary (or libraries/header files) into PREFIX/bin, PREFIX/lib or PREFIX/include for example when you run "make install".

ex:
```
./configure --prefix=/usr/
```

Note:
Try ```
./configure --help
```
It usually offers a lot of interesting options and help. :)

---

### Post by stimpak on 2009-06-23
Most of the times, i dont use the prefix when configuring, thus it get installed to the default dir, which can be whatever. I want to keep all as much humanly possible organized. 

So the proper prefix is /usr/ ?:confused:

---

### Post by KIAaze on 2009-06-23
As far as I know, the most common prefixes used for installations from source are:
```
/usr
/usr/local
/opt
/opt/shared
```

/usr is often the default and is where debian packages usually put their binaries. So in that sense, yes, it's the proper prefix.

cf also:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

You can also set the prefix to somewhere in your home directory, so you don't need the root password and keep your root system clean.
For libraries, I recommend using /usr or /usr/local, because otherwise, you'll have to set LD_LIBRARY_PATH to use them.

---

