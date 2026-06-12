---
title: "Belkin Wireless G Adapter"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by ACoppard on 2008-01-13
Where can I find drivers for this device, that work with Linux. Obviously, I will need to be able to run these from a USB Key Device, and then use a command to run them from there, as it cannot get on to the net at the mo?

Could I use the CD provided (Win only)

---

### Post by heindsight on 2008-01-13
going to need more info to be able to answer that one, mate.

Exactly what model is the device? Is it PCI or USB? What chipset does it use?
perhaps post the output of lsusb (or lspci if its a PCI device) here.

What version of Ubuntu are you using? 32bit or 64bit?

---

### Post by ACoppard on 2008-01-13
ur, ok. going to try and stumble through

I have followed the RT73 install post, and it didn't work.

Its a USB device, Belkin F5D7050 Wireless G USB device, clueless as to the chipset.
Ubuntu 6.10 Edgy Eft

LSUSB:
Bus 001 Device 005: ID 050d:705e Belkin Components
Bus 001 Device 002: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 001 Device 001: ID 0000:0000

---

### Post by ACoppard on 2008-01-13
So, i managed to install it via NDISWRAPPER. It now shoiws up in the config manager, but now will not connect to the net or any network resources (network apssword is off, ip address is static, and dns and gateway checked, rechecked and then checked again). Any ideas?

---

### Post by ACoppard on 2008-01-14
Anyone?
I have run iwconfig, and can't seem to make heads or tails of it, but it does tell my adapter is @ wlan0. I used ubuntu's networking tools to give it the password of nothing (as in no characters or numbers), added the essid (coppardnetwork) gave it the IP Address 192.168.2.23, Subnet, 255.255.255.0, Gateway of 192.168.2.1 and the DNS servers of 212.74.112.66 and 212.74.112.67 (the same setting as my Windows PC, apart from the IP address, obviously ;-)

---

### Post by commonplace on 2008-01-14
Have you tried following the howto in [this thread]("http://ubuntuforums.org/showthread.php?t=563547")?

/Kevin

---

### Post by rustybronco on 2008-01-14
If you have a chipset that uses the rt73 driver, and I believe you do have an rt73 [http://ubuntuforums.org/showthread.php?p=4124052](http://ubuntuforums.org/showthread.php?p=4124052)
try this thread "exchanging" the correct daily cvs for your chipset.
[http://ubuntuforums.org/showpost.php?p=3609183&postcount=1](http://ubuntuforums.org/showpost.php?p=3609183&postcount=1)
daily cvs is available from here. [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)
let us know if it works.

---

