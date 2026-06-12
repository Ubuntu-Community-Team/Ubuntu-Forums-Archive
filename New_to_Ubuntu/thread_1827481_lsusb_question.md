---
title: "lsusb question"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by gunneronaspooky on 2011-08-18
I am still pretty new to Linux, but i'm learning. I'm also working on learning Android at the same time...so here's my question...

I have my ASUS Transformer hooked up in APX mode(basically recovery mode). When I run lsusb, it shows that it is connected as bus 002 device 004. I am trying to run ```
lsusb -v
``` ( I'm helping a dev to work on looking for an exploit that will give us root), but when I run lsusb -v, it seems to be giving me the info for my built in webcam....how do I point it in the direction of the Transformer? Thanks in advance.

Edit : USB debugging is turned on for the Transformer

---

### Post by mcstat on 2011-08-18
I'm not that much of a computer guy so pardon my reply if is silly. Just try lsusb only and it will identify all the connected usb devices then you can identify the address of the transformer.

---

### Post by anewguy on 2011-08-18
Do just the lsusb first to get the man:dev id's, then do the lsusb -v on just that device.  What you will probably see are several endpoints - the technical documentation for the device should tell you which endpoint(s) you need, however you may need to contact the manufacturer to see if you can get such information.

To access the endpoints you'll need to use the libusb calls - be sure to install the libusb development lib and check out the documentation.

---

