---
title: "Can't get ubuntu 10.10 to reconize and mount my camera"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by rsaganek on 2010-11-29
bobby@bobby-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 010: ID 2525:8901  
Bus 004 Device 003: ID 0a48:3239 I/O Interconnect Multimedia Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 011: ID 040a:0585 Kodak Co. Digital Camera
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

That is what i get when i run lsusb... I"m so lost and new to the console that its making me mad... I hope some one can help... the main error it is giving me is unable to mount camera and then i can't read any of my pictures on the camera... wife mad... need help quicks

---

### Post by TopEnder on 2010-11-29
> **rsaganek said:**
> bobby@bobby-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 010: ID 2525:8901  
Bus 004 Device 003: ID 0a48:3239 I/O Interconnect Multimedia Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 011: ID 040a:0585 Kodak Co. Digital Camera
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

That is what i get when i run lsusb... I"m so lost and new to the console that its making me mad... I hope some one can help... the main error it is giving me is unable to mount camera and then i can't read any of my pictures on the camera... wife mad... need help quicks
Hi, Does the camera have a memory card installed and the photos are on the card, if so you could use your multimedia card reader to access the photos.

---

### Post by C!pheR on 2011-03-04
Did you get this resolved? I'm having the same issue with my Panasonic TZ-7. 

> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 1532:0200 Razer USA, Ltd 
Bus 003 Device 004: ID 050d:0815 Belkin Components Nostromo n52 HID SpeedPad Mouse Wheel
Bus 003 Device 003: ID 04b4:1220 Cypress Semiconductor Corp. 
Bus 003 Device 002: ID 1532:0103 Razer USA, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**EDIT**
PEBKAC - Problem Exists Between Keyboard And Chair. I've fixed this now by pressing the button on my camera that says "Connect to PC"...

:lolflag:

---

### Post by Lucradia on 2011-03-04
If the camera allows you to choose between identifying as a camera, or as storage, please make sure that it identifies as storage. If the OP is still having problems, that is.

---

### Post by deconstrained on 2011-03-04
Yeah, could always be an issue with the configuration of the device itself. Furthermore...You don't really need to mount the camera. 

There exist drivers and utilities for accessing a digital camera without mounting it (and at higher speeds than if it were mounted). Shotwell seems to do this sort of thing; when my camera mounts it asks me to dismount it before importing photos. And damn, it imports fast; 10-20 1+ MB photos usually take less than three seconds. Best speeds I've ever seen importing by drag & drop have been dismal by comparison.

---

### Post by mcduck on 2011-03-04
...and there's always the best option, getting a card reader and plugging the card into that instead of accessing it through the camera.

Pretty much every digital camera is *horribly slow* to transfer data compared to what you get from the card itself, and as a bonus you never need to worry about compatibility issues and you don't need to have the camera sitting on your desk and powered up to transfer images from it.

Apart from tethered shooting and such tasks, there really isn't much reasons to connect a camera to a computer. At lest until some camera manufacturer starts paying even the smallest bit of attention to their USB connection speeds. And even then a simple card reader would provide better compatibility and less problems.

---

