---
title: "USB MP3 Player not found"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Scarath on 2009-02-24
Hi
I am having a problem with a USB stick mp3 player. 
The Mp3 player needs reformatting but is is not recognised by my ubuntu install as a flash drive. It used to work and my PC can see other flash drives. Gparted does not see it. 
When I plug it into a windows install windows can see an mp3 player has been plugged in but cannot do anything with it (doesnt show up on the storage manager either).
I did 'lsusb' but it wasnt much help in finding it:

```
Bus 008 Device 008: ID 062a:0201 Creative Labs Defender Office Keyboard (K7310) S Zodiak KM-9010
Bus 008 Device 007: ID 046d:c508 Logitech, Inc. Cordless Trackball
Bus 008 Device 006: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 008 Device 005: ID 07ab:fcdf Freecom Technologies
Bus 008 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 008 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 008 Device 002: ID 163f:1611
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f3:0103 Elan Microelectronics Corp.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

greatful for any advice

---

### Post by llamabr on 2009-02-24
Plug it in, wait a minute, and post the last few lines of dmesg

Also, depending on what type of mp3 player it is (you didn't say), you may need to change it from usb mode to msc.  It will have to be in the latter to be seen automatically.

---

