---
title: "ndiswrapper wusb54g No ip?"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by heri0n on 2007-05-03
Hey guys, I was using dapper and decided it was time to upgrade to feisty
Just trying to get my wireless setup..
I installed ndiswrapper and it looks like it installed properly... i can see the access point 
The thing is, I don't seem to get an IP address and I can't load any websites
I do an ifconfig and theres no ip for rausb0 
I put it on dhcp
Any advice?

---

### Post by heri0n on 2007-05-04
bump

---

### Post by Floppyjoe on 2007-05-04
> **heri0n said:**
> Hey guys, I was using dapper and decided it was time to upgrade to feisty
Just trying to get my wireless setup..
I installed ndiswrapper and it looks like it installed properly... i can see the access point 
The thing is, I don't seem to get an IP address and I can't load any websites
I do an ifconfig and theres no ip for rausb0 
I put it on dhcp
Any advice?
Did you blacklist the rt2570 driver?
I have a tutorial for WUSB54G v4 here:
[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=21](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=21)
It's for edgy but it should probably work for Feisty too.

---

### Post by heri0n on 2007-05-04
I have blacklisted it..
I ran the tutorial in the sticky which looks pretty much the same as yours

---

### Post by heri0n on 2007-05-04
and another thing..
when i do iwconfig for access point it says not associated but the essid is the right ap..

---

### Post by Floppyjoe on 2007-05-04
Well I have this device on one of my sisters computers running edgy. I have not tried to upgrade that computer yet. There may be some wireless issues that need to be ironed out still in Feisty. I have another dongle the D-link DWL-G122 H/W vC1 that does not work in Feisty Like it did for me in Edgy.

---

### Post by heri0n on 2007-05-04
well it looks like its working for a lot of other people..
and is ndiswrapper not included on the feisty cd.. i cant seem to find it in synaptic

---

### Post by heri0n on 2007-05-04
i was originally using ndiswrapper-1.43.tar.gz from ndiswrapper website
i just tried uninstalling it and using 1.9 from [http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)
i got up to sudo ndiswrapper -i rt2500usb.inf
but when i try to modprobe ndiswrapper
i get.. is the kernel module not included in the package??
FATAL: Could not open '/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko': No such file or directory

---

### Post by heri0n on 2007-05-04
okay i tried the original rt2570 driver that i blacklisted..
when i look at the access points available though it shows the one i use as 0%
but when i do iwconfig 
the essid is right and the access point actually has a mac address now..
and the link quality was 70/100 around...
but i still cant use the internet
and ifconfig shows another interface rausb0:av i think it was..
the ip address is 169.something but that isn't right it should be 192. something

---

### Post by heri0n on 2007-05-04
bump

---

### Post by PARO on 2007-05-05
you need ndiswrapper-common also, make sure you have that as well as the utils.  Floppyjoe's tutorial worked on feisty for me with those both installed, and using his drivers. Good luck.

---

