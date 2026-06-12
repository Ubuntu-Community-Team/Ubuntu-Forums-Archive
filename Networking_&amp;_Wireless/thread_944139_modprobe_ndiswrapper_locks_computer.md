---
title: "modprobe ndiswrapper locks computer"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by snakep on 2008-10-11
Hello, I am having trouble getting a Broadcom BCM4318 card to work with ndiswrapper.  I am running 8.04 on a Compaq V2000 laptop.  I have installed ndiswrapper and followed instructions on several threads and how-to pages, and several of them tell me to issue the following commands in order:

```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy 
sudo rmmod wl 
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
```

Everything works fine until I get to "modprobe ndiswrapper", which causes the computer to completely lock.  If I run the command without first running "rmmod ndiswrapper" it seems to execute, but the wireless card is still reported as unclaimed in "lshw -C network".  

What could be causing the computer to lock up?  Is there a way to retrieve the log after I've forced it to reboot?

Thanks,

Jeremiah

---

### Post by snakep on 2008-10-11
Does anybody have any suggestions?  I am on the verge of giving up on Ubuntu.

---

### Post by kevdog on 2008-10-11
Likely the driver you are wrapping inside ndiswrapper is incorrect for your network card!!

---

