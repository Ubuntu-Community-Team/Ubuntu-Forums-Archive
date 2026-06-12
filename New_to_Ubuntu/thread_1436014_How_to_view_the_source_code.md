---
title: "How to view the source code"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by nmakkena on 2010-03-22
Hi
I am very new to linux and i have recently installed ubuntu 9.10. I just wanted to know how to view the source code. please let me know how to view the source code.

---

### Post by Alias1407 on 2010-03-22
It depends on what you're talking about....

Ubuntu is basically just a collection of programs that are configured in a certain way. You will have to download the source code for the individual programs to view the source. If you want to view the source of the Linux Kernel itself then goto [http://kernel.org](http://kernel.org)

---

### Post by amauk on 2010-03-22
you can get the source code for individual packages by doing
```
apt-get source <package>
```

*edit*
If you're planning on compiling things,
also do
```
sudo apt-get build-dep <package>
```
this installs any extra stuff needed (gcc, and any dev libraries for example) to build the source of a particular package
*edit*

Ubuntu also provides a source CD for every release
Eg. this is the Karmic source CD
[http://cdimage.ubuntu.com/releases/karmic/release/source/](http://cdimage.ubuntu.com/releases/karmic/release/source/)

as you can see, it's huge
the "normal" CD (pre-compiled) is 700Mb
the source CD is 2.5Gb

---

