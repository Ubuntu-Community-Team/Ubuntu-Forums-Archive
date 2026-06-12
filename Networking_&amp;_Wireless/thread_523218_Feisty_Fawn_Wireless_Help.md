---
title: "Feisty Fawn Wireless Help"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by dfetz88 on 2007-08-11
I am pretty new to Linux and just installed Feisty Fawn.  I am trying to get my linksys wireless b usb adapter to work.  it is wusb ver 2.6 can anyone help me please

---

### Post by kevdog on 2007-08-11
Thats a pretty old adapter.  I looked for a while and the only thing I could come up with was this link:
[http://at76c503a.berlios.de/](http://at76c503a.berlios.de/)

It requires however that you need to download the source files and then compile and install them.  Im not sure if you know how to do this.

The only other thing I might try first is typing
sudo aptitude install atmel-firmware 
at the command line, rebooting with the device plugged in and see what happens.  If you get nothing, check dmesg to see if anything pops up.  I think this only gives a solution for pci devices rather than usb, but I could be wrong, and there is no harm in trying!!

---

