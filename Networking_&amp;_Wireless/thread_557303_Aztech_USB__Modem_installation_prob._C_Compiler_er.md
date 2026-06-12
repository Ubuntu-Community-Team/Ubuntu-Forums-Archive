---
title: "Aztech USB  Modem installation prob. C Compiler error.."
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by arvin2212 on 2007-09-22
hey guys,,, been using ubuntu all this while and it seems great.. but only 1 prob..installing my usb modem... :D

well this is what i did according to the instructions give in the modem's cd.

1. i copied the "eagle-usb-2.0.0.tar" file to the root directory according to the manual.
2.i opened the terminal and typed "tar -jxvf eagle-usb-2.0.0.tar.bz2"
3. The "eagle-usb-2.0.0.tar" file begins to extract.
4. Then i typed "cd eagle-usb-2.0.0" according to the manual.
5. Then i typed "./configure –enable-cmv" according to the manual.

The problem starts at step 5 where i get this error:

```
root@ubuntu:~/eagle-usb-2.0.0# ./configure –enable-cmv
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: –enable-cmv
checking for –enable-cmv-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

I tried checking all over the net.. looking for solutions.. tried various other ways but all of it were unsucessful. 
:(

--------
Read somewhere and some1 gave a solution where i have to download "linux-image-2.6.20-15-generic_2.6.20-15.27_i386.deb" and install it.. tried it but i still get the same error as above even after installing.


This is the version of my kernel =2.6.20-15-generic

. and guys i cant use the internet while in ubuntu so i cant use the commands to download stuff.:D

hope  u guys would be able to help me.. :D

---

