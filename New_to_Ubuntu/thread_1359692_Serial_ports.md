---
title: "Serial ports"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2009-12-20
So I've noticed that a lot of times when I'm using usb-to-serial adapters that linux will create multiple ttyACM* files in /dev.

For instance say I'm interfacing with /dev/ttyACM0 and short a pin out on my setup and the serial program (gtkterm) is monitoring it.  Well then my device crashes, and reboots.

But upon reboot it will decide to be /dev/ttyACM1 or /dev/ttyACM2, etc.  So I have to use those instead of ACM0.  So after a few of these I get lots of ACM files that do nothing.  

How do I even get rid of the other ones?  It sort of makes serial programming hard to do when I'm experimenting a lot and keep having to change my port names.

---

