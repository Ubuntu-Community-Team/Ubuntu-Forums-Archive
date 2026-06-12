---
title: "Shuttle PN15 USB Wireless Driver"
date: 2005-06-30
forum: Networking &amp; Wireless
---

### Post by Jæd on 2005-06-30
Hi,

I'm trying to install the Shuttle PN15 wireless driver. Has anyone managed to install this...? Where do I set the KERNAL_SOURCE line to in the MakeFile...? 

The example is:

KERNEL_SOURCE=/lib/modules/2.6.9-1.667/build/

But for my 2.6.10.5 I don't have this directory. How do I get it...?

Cheers...!

---

### Post by Jæd on 2005-06-30
Ok... I worked out that build was just a sym link to the src. Tried to compile the driver but it had lots of errors. I've tried ndiswrapper but after I do sudo modprobe ndiswrapper I don't get the interface appearing:

/var/log/messages:

Jun 30 18:31:28 bigbox kernel:
Jun 30 18:31:28 bigbox kernel: zd1211u: probe of 5-6:1.0 failed with error -22
Jun 30 18:31:28 bigbox kernel: usbcore: registered new driver zd1211u
Jun 30 18:31:28 bigbox kernel: ndiswrapper: driver zd1211u (WLAN,11/29/2004,2.23.1129.2004) added

I've looked in System -> Admin -> Networking and I just get eth0...

---

### Post by Jæd on 2005-06-30
Ah... I forgot to download kernal headers. The shuttle driver compiles and I can load the module. Now what... Still can't see the network card...

---

### Post by dogacres on 2008-05-09
I'm having the same problem now with Ubuntu 8.04/HH on my PN15-equipped Shuttle as you had several years back.

Were you every able to get wireless networking on-the-air?

---

