---
title: "How to install a scanner, medion life P91010"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by pfum on 2009-04-21
hi,
I've just started using Ubuntu 8.10 and i can't find how to install my scanner(it's a medion P91010), i have the installation cd but can't find how to install it...
 
Thx for helping.

---

### Post by juancarlospaco on 2009-04-21
Turn on and connect it, then open X-Sane.

---

### Post by halitech on 2009-04-21
> **juancarlospaco said:**
> Turn on and connect it, then open X-Sane.

in a perfect world that should be enough :)

first, open a terminal and post the results of
```
lsusb
```so we can see if the scanner is recognized. If it is, try to run
```
sudo sane-find-scanner
```
hopefully this will come back with some info thats useful like this.
>  found USB scanner (vendor=0x05da, product=0x3025, chip=SQ113?) at libusb:002:006 found USB scanner (vendor = 0x05da, product = 0x3025, chip = SQ113?) at libusb: 002:006  
 found USB scanner (vendor=0x0ccd, product=0x003c) at libusb:002:004 found USB scanner (vendor = 0x0ccd, product = 0x003c) at libusb: 002:004 

if that works, then try this```
scanimage-L 
```
if all goes well, you should then be able to open xsane and be able to scan.

---

### Post by Cresho on 2009-04-21
ya!  just turn it on and use xsane  which is under graphics.

---

### Post by pfum on 2009-04-24
hello everyone , apparently it doesn't recognize it,

and when i run the sudo sane-find-scanner i get
 
"found USB scanner (vendor=0x05da [Prolific Technology Inc.], product=0x3025 [USB Scanner               ], chip=SQ113) at libusb:004:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L "

and with scanimage -L i get:

 "No scanners were identified."

---

