---
title: "need help setting up wireless - bcm4310"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by sleimson on 2008-09-18
Hi all!

Im seriously frustrated trying to get my wireless setup. I have followed countless instructions and still have no wireless. I know I have installed the correct driver from the ndiswrapper -l command

lshw -C network issues the following: 

  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0


I am guessing the UNCLAIMED bit is what I have to work around.

also, I am getting alot of 'unknown symbols' when I type in - dmesg | grep -e ndis -e wlan

Any ideas?

---

### Post by Ayuthia on 2008-09-18
> **sleimson said:**
> Hi all!

Im seriously frustrated trying to get my wireless setup. I have followed countless instructions and still have no wireless. I know I have installed the correct driver from the ndiswrapper -l command

lshw -C network issues the following: 

  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0


I am guessing the UNCLAIMED bit is what I have to work around.

also, I am getting alot of 'unknown symbols' when I type in - dmesg | grep -e ndis -e wlan

Any ideas?

ndiswrapper does have some complications with this chipset.  Your card should have worked with the wl driver.  If you have a wired connection, you can run the updates and it should work (of course you will have to blacklist ndiswrapper for it to work).  Either that or you can install 8.04.1 and that should make it work also.

---

### Post by sleimson on 2008-09-18
hey thanks, I might update to 8.04.1. Sure I have got latest updates of ndiswrapper tho. 

 I think one of my problems was that I was using Vista driver.

changing to xp. 

rakan@rakan:~$ dmesg | grep -e ndis -e wlan
[   33.460927] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   33.536317] usbcore: registered new interface driver ndiswrapper

I am expecting to see some sort of associationo betee ndiswrapper and wlan0.

---

### Post by Ayuthia on 2008-09-18
> **sleimson said:**
> hey thanks, I might update to 8.04.1. Sure I have got latest updates of ndiswrapper tho. 

 I think one of my problems was that I was using Vista driver.

changing to xp. 

rakan@rakan:~$ dmesg | grep -e ndis -e wlan
[   33.460927] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   33.536317] usbcore: registered new interface driver ndiswrapper

I am expecting to see some sort of associationo betee ndiswrapper and wlan0.

I think I miscommunicated.  I meant that if you have the latest Ubuntu updates, the wl driver should work for you.  I am guessing that Ubuntu is not up to date yet because you are still listing your card as a 4310 instead of a 4312.

You are heading on the right track with ndiswrapper.  You cannot use Vista drivers.  There are only a limited number of XP drivers that do work with your card though.  You can check:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
It has a link for your card that might work.

You will also need to blacklist the wl driver if you have not done so already.  Your Broadcom card is a little different than the others in Ubuntu because Broadcom made a Linux driver for your card.  If you want to blacklist it:
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist
```

Once you have the driver loaded (ndiswrapper -i bcmwl5.inf) and loaded the ndiswrapper module (sudo modprobe ndiswrapper), you can check and see if the module loaded:
```
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e wl
lshw -C network
```
The first command should only return values with ndiswrapper.  If you see results that contain bcm43xx, b43, ssb, or wl, the ndiswrapper module might not work properly.

The second command will show you in the driver= section what driver it is trying to use.  If it shows ndiswrapper, then things are working.

Hope that helps.

---

### Post by sleimson on 2008-09-18
Thanks Ayuthia..

all sorted now using the link u provided.. the ultimate issue was the driver i was using.

---

