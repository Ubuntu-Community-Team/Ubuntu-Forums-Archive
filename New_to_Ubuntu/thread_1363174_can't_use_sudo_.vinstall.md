---
title: "can't use sudo ./vinstall?"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by Tomdev on 2009-12-24
Hey everyone,

I'm new to linux but I wanted to install a driver for my video card because I had no 3d with the standard driver(I have a via chrome9 graphics chip). So I downloaded the driver and extracted it. In the extracted map there was a vinstall which I had to run to install the driver. So what I did was:
-open a terminal
-cd to the extracted map
-type sudo ./vinstall

then I got this error: 
```
tom@tom-desktop:~/Bureaublad/test1$ sudo ./vinstall
sudo: ./vinstall: command not found
```does someone know what I'm doing wrong here:confused: 

Tomdev

PS: sorry for my english

---

### Post by wojox on 2009-12-24
It looks like your in the wrong directory. If you list the directory does it show and is it executable?

---

### Post by Tomdev on 2009-12-24
thanks making it executable worked:P

Tomdev

---

