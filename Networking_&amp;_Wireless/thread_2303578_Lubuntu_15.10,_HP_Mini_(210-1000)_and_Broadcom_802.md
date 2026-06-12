---
title: "Lubuntu 15.10, HP Mini (210-1000) and Broadcom 802.11"
date: 2015-11-19
forum: Networking &amp; Wireless
---

### Post by user_289531 on 2015-11-19
I am currently allowing the  "Additional Drivers" to 'apply' the changes made when I clicked on the options given for wi-fi connectivity.

But, in case this attempt fails.

All I need to know is how can I make the wi-fi connection work on this laptop. That is all. I appreciate any feedback, thank you.

---

### Post by Bucky Ball on 2015-11-19
Welcome. You need to be online with a cable to install the Additional Drivers for you wifi. After that is complete, unplug the cable and reboot. Anything? If wifi not working, post the output of this command between code tags (see last link in my signature).

```
sudo lshw -C network
```

Due to the absence of any information about your card in your first post there is no way of telling you at this point how you would get it working. Once you know which wireless card you are using you will find lots of information about it and ubuntu online and by asking questions here.

---

### Post by user_289531 on 2015-11-19
*-network               
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eno1
       version: 02
       serial: c8:0a:a9:39:e0:e0
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.23 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:26 ioport:5000(size=256) memory:50010000-50010fff memory:50000000-5000ffff memory:57000000-5700ffff
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:56000000-56003fff

---

### Post by Bucky Ball on 2015-11-19
With the ethernet cable plugged in so you are online, do:

```
sudo apt-get update
sudo apt-get install firmware-b43-lpphy-installer
```

If that fails, try the instructions in post #8 [here]("http://ubuntuforums.org/showthread.php?t=2303454&p=13393630&viewfull=1#post13393630").

---

### Post by user_289531 on 2015-11-19
Thank you, I will give it a try because the "Additional Drivers" is taking way too long to apply the changes. I have been waiting for over 30 minutes and it is still barely loaded or yet to apply anything.

This is what I got in the terminal:

$ sudo apt-get install firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firmware-b43-lpphy-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  firmware-b43-installer

E: Package 'firmware-b43-lpphy-installer' has no installation candidate

The instructions in the link did not work either. the third step asked me to:

Media change: please insert the disc labeled                                   
 'Lubuntu 15.10 _Wily Werewolf_ - Release i386 (20151021)'
in the drive '/media/cdrom/' and press enter

The problem here is that the HP Mini is a netbook, and I do not have a CD drive. I installed Lubuntu via a flash-drive.

Scratch that, I just rebooted my netbook and it seems that now the wifi is working.

Thanks for your help! I just wish I knew exactly what code it was that did the trick. I suppose I could always just follow the suggestions here...

Thanks again!

---

### Post by Bucky Ball on 2015-11-20
Probably the first set of instructions did the trick after a reboot. If you can reboot and wireless is still working, please see the first link in my signature. :D

---

### Post by Bucky Ball on 2015-11-20
Don't know what did the trick. Might have happened at reboot. If you can reboot again and wireless is still working, please see the first link in my signature. :D

---

