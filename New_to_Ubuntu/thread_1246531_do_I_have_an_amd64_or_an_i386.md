---
title: "do I have an amd64 or an i386"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by RabbitWho on 2009-08-21
I'm trying to download this package:

[http://packages.ubuntu.com/jaunty/wvdial](http://packages.ubuntu.com/jaunty/wvdial)

To get mobile broadband to work on Kubuntu
(on the advice of this thread: 
[http://ubuntuforums.org/showthread.php?t=1223769](http://ubuntuforums.org/showthread.php?t=1223769))

Here are some of my laptop's specs, I don't know what's relevant. ( i read a little about these two thingys on wikipedia but am no closer to understanding what they are)

Intel® Pentium® Dual-Core Processor T4200 (2.0GHz, 800MHz, 1MB cache)
4096MB 800MHz Dual Channel DDR2 SDRAM [2x2048]
320GB (5,400rpm) Serial ATA Hard Drive

---

### Post by JDShu on 2009-08-21
open up a console, and type in "uname - m" without the quotes to find out the architexture... x86 is i386, x86_64 is amd64

---

### Post by jerrrys on 2009-08-21
in terminal enter **lshw  **and thats a small L.  also **sudo lshw** will give more info

---

### Post by RabbitWho on 2009-08-21
Got it! Thanks


It says.. i686... odd.. so I'll go with the i386 option. 

Thanks again :)

---

