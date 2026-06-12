---
title: "wine wont work"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by jonpon on 2010-02-08
Hi there,
Im having problems with wine, I have installed it,but it crashes when I click on any of the buttons.
If I us it as root it doesn't crash but still I cant run .exe files it says "opening " but does nothing. 

Could it be that I need specific hardware for wine to work? my old computer couldn't handle goodle earth for example because of an incompatible  graphics card

---

### Post by Cabs21 on 2010-02-08
what version of wine are you using?  enter into terminal
```
wine --version
```

---

### Post by jonpon on 2010-02-08
I'm using
wine-1.1.37

on ubuntu 8.10

---

### Post by Cabs21 on 2010-02-08
try using the 1.0.1 version.  It is more stable and will probably work better on the older OS.

---

### Post by Sir Jasper on 2010-02-08
Hi,

If you are not confident that the exe files you tried are expected to work in Wine then you could download a portable windows program (say, abiword) from [http://portableapps.com/](http://portableapps.com/)

Install it in your Home directory and click on the exe which works in Wine. If you want to get shot of it just delete it.

My regards

---

### Post by jonpon on 2010-02-08
Thanks guys
I'll try these ideas out

---

### Post by jonpon on 2010-02-08
I'm installing the 1.0.1 version as suggested and was prompted to install a few missing thing as I went along, now I got this message
> configure: error: X development files not found. Wine will be built
without X support, which probably isn't what you want. You will need to install
development packages of Xlib/Xfree86 at the very least.
Use the --without-x option if you really want this.

I searched synaptic for the xlib files but there are hundreds! does anyone know what I might need?
It also mentions mingw32 as missing. does anone know what that is?****

---

