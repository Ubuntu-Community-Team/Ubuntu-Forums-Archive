---
title: "cannot install dlink dwa 111"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by cementbag on 2007-10-20
have recently purchased wireless router with usb adapter, installed the router to my desktop PC ok but when I tried to install the usb dlink 
dwa111 wireless adapter to my laptop it keep saying theres a fault and cannot install device any ideas

---

### Post by hansson_14 on 2007-10-29
I have the same problem.

I kind of took the chance that the chip should be rt73, so I followed the instructions  in a How-to on a forum here. I tried it on 2 computers, both with Ubuntu 7.10 386.
When I try ifconfig -a there is no wlan1, only eth0 and lo.

Any clues?

/Fredrik

---

### Post by Nonsense on 2007-12-23
Same here.
No luck yet.

---

### Post by allvar on 2008-01-02
Same problem here.
I've downloaded the latest windows drivers from DLINK, installed ndiswrapper and manually added the drivers with ndiswrapper -i. Everything looks good in ndiswrapper -l.

However, when i do modprobe ndiswrapper the system actually hangs. Only way out of the hang is doing a hard reset.

Any ideas?

---

### Post by zenon_666 on 2008-06-11
Hi,


It works with latest rt73-cvs-daily.tar.gz.

More info: 
[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=8&t=4847](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=8&t=4847)

---

