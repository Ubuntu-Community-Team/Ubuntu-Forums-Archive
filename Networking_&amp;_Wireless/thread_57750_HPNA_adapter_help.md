---
title: "HPNA adapter help"
date: 2005-08-17
forum: Networking &amp; Wireless
---

### Post by aaron.gilbert on 2005-08-17
I am extremely new to the linux world, dabbled in it a little bit at school but no other linux distro seems to support my HPNA broadcom iLine10 network card.  Ubuntu (newest version) loads the drivers for the card just fine and it shows up in the device manager.  Only problem is, the device doesnt turn on when i turn the computer on.  The device works fine on my windows OS (how im posting now) and in order for me to be on the net with Ubuntu i need the Broadcom card to start so i can make it one of my network choices.  

any help is greatly appreciated and loved.

thanks to everyone or anyone!

---

### Post by aaron.gilbert on 2005-08-18
anyone at all?

---

### Post by aaron.gilbert on 2005-09-07
/bump

---

### Post by lompolo on 2005-09-07
I think this is solved long time ago.

Common hint. Try search homepna in this forum.
(try using livecd. I think homepna works with Warty livecd -not hoary-)


Open terminal. Applications -> System tools -> terminal

sudo gedit /etc/modules

then add
eth0 homepna=1 
pcnet32 homepna=1

save 
quit
exit from terminal
then reboot and light goes on


I hope Breezy would autodetect homepna cards without editing /etc/modules.

---

### Post by plbee on 2007-07-12
Has anybody found a way to make Netgear 101 HPNA USB network adapters to work? It is not seen in network manager at all. It shows up as netgear X10 USB adapter with 'unknown' in all the fields. Is there perhaps a driver available?
Thanks all. PB

---

