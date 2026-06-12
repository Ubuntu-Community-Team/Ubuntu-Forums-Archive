---
title: "[SOLVED] Ndiswrapper and SSB confilct at startup!"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Crandom on 2008-05-02
For several hours I messed around with b43 and ssb to try to get my broadcom bcm4318MPG card to work, and all attempts failed. Then I managed to get it working using ndiswrapper and some windows firmware; however, at the start to start to get it working I have to use these terminal commands:
```
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```
then it configures itself and starts working properly. My "ndiswrapper -l" shows:
```
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
```
Notice the alternate driver that lead me to think of rmmod'ing it :)

The question is: how do I make it start working automatically without typing in the terminal commands? Do I have to blacklist ssb? Help!

Thanks in advance.

---

### Post by Ayuthia on 2008-05-02
Check out this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb)

This has the instructions on how you can get it to work on reboot.  Version 3 is new, but it should work.  I was working on a similar process, but I found that this post was faster than my research...

---

