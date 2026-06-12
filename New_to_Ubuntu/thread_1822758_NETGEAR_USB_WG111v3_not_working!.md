---
title: "NETGEAR USB WG111v3 not working!"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by david476 on 2011-08-11
I recently bought a netgear wireless-g USB 2.0 adapter WG111v3 and I cannot figure out how to make it work in Ubuntu 11.04

_***SOLVED!***_

---

### Post by amjjawad on 2011-08-11
> **david476 said:**
> I recently bought a netgear wireless-g USB 2.0 adapter WG111v3 and I cannot figure out how to make it work in Ubuntu 11.04

Hello and Welcome :)

From Terminal, please run the below command and post the output here and please wrap up the output with "CODE" tags or highlight the text and click "#".

```
sudo lshw -C network

```

---

### Post by anewguy on 2011-08-11
If you have the ability to temporarily hard-wire your PC to the router, please do the following:

- hard-wire to the router
- open a terminal window and type:

sudo apt-get update <press enter>

- go to additional drivers - it may take a little while, and see if it comes up with a driver you can enable. 

Chances are the above won't work for this adapter.  I used to run this adapter in my old PC, and it worked fine, but doing the above it still never found a driver.  I had to download the driver from Netgear's site - and be ****sure**** to download the driver for the version 3 board.

Next you need to install ndiswrapper and ndisgtk - if you have a hard-wired connection you can do this with the package manager.  If not, post back and I'll walk you through installing from the LiveCD or a LiveUSB media.  You may have seen people reporting ndiswrapper to be a nightmare - ignore them.  When you use the graphical front-end ndisgtk nothing could be simpler and in the case of this adapter it is how to get it to work (unless something has drastically changed since about 5 months ago when I still ran the adapter).  After you get, or need help installing, ndiswrapper and ndisgtk just post back - it's very simple to use but let's handle one hurdle at a time.

Dave ;)

---

### Post by david476 on 2011-08-11
amjjawad: I got:

*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 8c:89:a5:10:45:3f
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:e000(size=256) memory:d0004000-d0004fff(prefetchable) memory:d0000000-d0003fff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: c4:3d:c7:75:4a:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
anewguy: I got a bunch of errors. (I was not exactly clear on what to do):confused:

---

### Post by uRock on 2011-08-11
**sudo apt-get install linux-firmware-nonfree** is what I used to get my netgear wireless working.

---

### Post by david476 on 2011-08-11
URock:
what does the nonfree part mean, I'd prefer not to pay.

---

### Post by uRock on 2011-08-11
> **david476 said:**
> URock:
what does the nonfree part mean, I'd prefer not to pay.

Nonfree just means there is/was a EULA for the code in the package. No purchase necessary. :D

---

### Post by david476 on 2011-08-11
IT WORKS!!!!!!, thanks a lot!

---

### Post by uRock on 2011-08-11
Yay! You're welcome :D

---

### Post by amjjawad on 2011-08-11
Glad you managed to fix it and good to know the solution is just one line :)

Thanks uRock :)

---

### Post by anewguy on 2011-08-11
I've got to put this in the "remember" box so if I end up using that old PC again I can do this now instead of what I did.  Wish I had known then, but at the time nobody posted back so I guess nobody knew at the time.

Glad it's working for you, and glad others had a far easier way to get it working!

Dave;)

---

### Post by david476 on 2011-08-13
If you guys could help me on some other things that would be great, just search my username!

---

### Post by mojojag on 2011-11-21
I solved this problem by figuring out the kernel config options to use and then used an old ubuntu kernel config and just added the options, installed, regenerated initrd, and voila. It took me a week and a half. I could fix it for you in 15 min. plus build time.
-David

---

