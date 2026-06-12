---
title: "Really annoying rt2500"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by awalsh on 2007-10-23
Hello,

Im having some serious problems with my laptop and a Belkin F5D7010 (rt2500 chipset). It worked flawlessly in Feisty, just had to download the serialmonkey drivers and away you went. Now in Gutsy it appears to work for all of 30 seconds, eg I manually configure it via /etc/network/interfaces and the connection works fine at normal speed. I run apt-get update and it works, then suddenly the connection dies and will not recover (even a /etc/init.d/networking restart) will not fix it.

I have tried using ndiswrapper but the belkin website does not give the .inf file required to use ndiswrapper (just a .cat and .sys file). Every single version of Ubuntu from Breezy has had the same problem for me on this laptop and I have usually been able to fix it with serialmonkey drivers every time that it is claimed that "rt2500 is supported out of the box".

Not on a rant but its just annoying not having wireless connection, and I cannot even get a wired connection in Gutsy when plugged direct into my router. But thats another issue.

A little info:

**Laptop:** IBM Thinkpad R51e
**Card:** Belkin F5D7010 Version 3000uk PCMCIA
**OS:** Ubuntu Gutsy Clean Install (installed about 2 minutes ago)

If anyone could point me in the right direction I would really appreciate it, because currently I'm lost with no idea what I can do. (besides going back to feisty)

Thanks

Andrew

---

### Post by DrFreeze on 2007-10-23
i have a similar problem

i have a linksys wireless pci card with a rt25xx chipset, sometimes it will connect, work for a few minutes, then die, and no amount of tinkering with the configs will get it back up. In order for the system to get its wireless back i need to reboot.

the system log show a few errors along the line of:

wlan0:  duplicate address detected!
Please file a bug report to rt2x00.serialmonkey.com

and a number of lines like:

Unrequested down ?:3

Does anyone have a clue what is going on?

system specs:
Core 2 Duo e4300
MSI P6N-SLI
8800 GTS 320
ubuntu 7.10 32 bit

---

