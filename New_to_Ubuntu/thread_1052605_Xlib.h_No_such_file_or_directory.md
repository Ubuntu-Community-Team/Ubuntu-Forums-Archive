---
title: "Xlib.h: No such file or directory"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by gunterhausfrau on 2009-01-27
I'm trying to install something called morse2led. I believe that it is possible on ubuntu, but seem to be having difficulty. Please forgive my ignorance, but this is the error that I am getting.

root@Conroe:/home/dan/Desktop/morse2led-1.0# make
gcc -o blinker -O2 -Wall -L /usr/X11R6/lib/ -lX11 -I /usr/X11R6/include/  -DLINUX blinker.c
blinker.c:34:22: error: X11/Xlib.h: No such file or directory
blinker.c:117: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token

so I believe that a required header file Xlib.h is missing, I've looked about and can't find it "locate Xlib.h" nothing. Should this be installed as default with ubuntu? or am I missing something? (I'm missing many things) but what specifically am I missing?

If I look in the X11R6 directory all I see is the directory "bin"

Thanks.

---

### Post by Sorivenul on 2009-01-28
Try:
```
sudo apt-get install libx11-dev
```

Then try your compile again.

---

### Post by gunterhausfrau on 2009-01-28
yep, that's what did it.

Thanks.

---

### Post by brent.of.all.people on 2009-08-13
> **gunterhausfrau said:**
> yep, that's what did it.

Thanks.

Hey,

I'm trying to get the morse2led package to work too. I got it to compile and install, but blinker doesn't seem to have any effect. Were you able to get it to work?

---

