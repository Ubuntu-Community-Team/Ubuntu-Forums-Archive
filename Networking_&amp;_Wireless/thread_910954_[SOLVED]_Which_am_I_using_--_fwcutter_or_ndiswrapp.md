---
title: "[SOLVED] Which am I using -- fwcutter or ndiswrapper"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by mikeeve on 2008-09-05
I've upgraded Ubuntu from feisty to gutsy to hardy. Every time, the wireless breaks (I have Broadcom 4306). Originally, I used ndiswrapper to get it working. This time, I  tried to use fwcutter. My wireless is WORKING now, but I'm not sure if I'm using ndiswrapper or fwcutter. How do I tell which is actually driving the wlan0?  

 I'm curious because when I click the Network Connection icon in upper right it shows wlan0, but then when I click on configure, I get "interface does not exist", but the wireless is working!

Sorry if this info is somewhere else in this forum, but after spending a couple of hours without finding the answer, I'm going to bed and hoping someone will have an answer for me tomorrow.  ](*,)

---

### Post by regala on 2008-09-05
> **mikeeve said:**
> I've upgraded Ubuntu from feisty to gutsy to hardy. Every time, the wireless breaks (I have Broadcom 4306). Originally, I used ndiswrapper to get it working. This time, I  tried to use fwcutter. My wireless is WORKING now, but I'm not sure if I'm using ndiswrapper or fwcutter. How do I tell which is actually driving the wlan0?  

 I'm curious because when I click the Network Connection icon in upper right it shows wlan0, but then when I click on configure, I get "interface does not exist", but the wireless is working!

Sorry if this info is somewhere else in this forum, but after spending a couple of hours without finding the answer, I'm going to bed and hoping someone will have an answer for me tomorrow.  ](*,)

hem, well, fwcutter is not a wifi driver, it is a tool to extract firmware parts from other-OSes drivers. don't understand what you want.

but please run lsmod in a terminal, and check for "ndiswrapper" in the list. if not present, you're clearly using b43 (and not fwcutter)

---

### Post by Ayuthia on 2008-09-05
If you type lshw -C network in the Terminal, it will let you know which driver it is trying to use for your network cards.

---

### Post by mikeeve on 2008-09-05
I thought that's all fwcutter did, but I wasn't sure since I ran it from a shell script. Years ago, I extracted the drivers for ndiswrapper using a copy of the drivers from my windows xp, but this time I let the script download new drivers.

ls mod does list ndiswrapper, used by 0.

lshw -C network lists:
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
 

So,  I take it I'm not using ndiswrapper, but somehow using the drivers in /lib/firmware ? 

Thanks, all.  ;)

---

### Post by Ayuthia on 2008-09-05
> **mikeeve said:**
> I thought that's all fwcutter did, but I wasn't sure since I ran it from a shell script. Years ago, I extracted the drivers for ndiswrapper using a copy of the drivers from my windows xp, but this time I let the script download new drivers.

ls mod does list ndiswrapper, used by 0.

lshw -C network lists:
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
 

So,  I take it I'm not using ndiswrapper, but somehow using the drivers in /lib/firmware ? 

Thanks, all.  ;)

You are correct!!!  Sorry, we are all out of prizes today though.

If you did not get any more information from lshw -C network, then you can try the following:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe ndiswrapper
```
This will only work for this session.  If it does work, we will need to blacklist b43 and ssb by doing the following:
```
echo blakclist b43 | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist
```
It might be possible that you might need to add ndiswrapper to /etc/modules:
```
echo ndiswrapper | sudo tee -a /etc/modules
```

---

### Post by mikeeve on 2008-09-05
In case I confused you, my wireless is working. 

And I've moved the other way by removing ndiswrapper from /etc/modules. lsmod no longer lists ndiswrapper.  I've rebooted and wireless is still working. b43 is not blacklisted. :roll:

Is there any reason I should use ndiswrapper for wireless instead of the current solution? 

I don't understand why I previously (fawn, gibbon) I needed ndiswrapper, but now I don't under heron.

---

### Post by Ayuthia on 2008-09-05
> **mikeeve said:**
> In case I confused you, my wireless is working. 

And I've moved the other way by removing ndiswrapper from /etc/modules. lsmod no longer lists ndiswrapper.  I've rebooted and wireless is still working. b43 is not blacklisted. :roll:

Is there any reason I should use ndiswrapper for wireless instead of the current solution? 

I don't understand why I previously (fawn, gibbon) I needed ndiswrapper, but now I don't under heron.

There is no real reason why you need to use ndiswrapper.  Some people have said that they have better speeds using ndiswrapper but if you are happy with the speed, then I would not worry.

The reason why you might have needed ndiswrapper in prior versions is because they have made improvements to the Linux open source Broadcom driver in the 2.6.24 kernel.  The bcm43xx module is replaced by the b43/b43legacy module.  It has improved speeds and more wireless card support than before.

Glad to see that it works!

---

