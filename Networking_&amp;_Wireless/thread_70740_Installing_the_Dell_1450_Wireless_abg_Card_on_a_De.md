---
title: "Installing the Dell 1450 Wireless a/b/g Card on a Dell Inspiron 9200 with Ubuntu 5.04"
date: 2005-10-01
forum: Networking &amp; Wireless
---

### Post by ajferrari on 2005-10-01
I have a fresh installation of Ubuntu 5.04. I did a standard "Linux" installation at the boot prompt before my install. I then proceeded to update my Linux installation through my LAN cable. I then downloaded the kernel source, gcc, g++, ndiswrapper source and utils through synaptic package manager. I then downloaded my Dell Wireless card driver which I have succesfully installed using ndiswrapper various times with various distro's (including Debian).

#Unzip R~~~~.exe
...
#ndiswrapper -i bcmlw5.inf
#ndiswrapper -l
bcmwl5 drivers present, hardware present
#modprobe ndiswrapper
 FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Anyone have any ideas? I tried the command ndiswrapper -m, however it doesn't work to produce a working network port. I am pretty sure my kernel has module support, why is this operation not permitted? Oh yeah, I am doing this in a root shell, and I did try the command:

#sudo modprobe ndiswrapper
# FATAL: Error inserting ndiswrapper #(/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): #Operation not permitted

I have read through some of the posts, but I decided to devote a forum specifically to this card.;-) Noone seems to have been able to solve the problem using the methods I have available given my situation! Anyone have any ideas?

---

