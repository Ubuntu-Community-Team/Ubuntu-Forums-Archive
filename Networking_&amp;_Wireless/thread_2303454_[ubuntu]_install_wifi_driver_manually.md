---
title: "[ubuntu] install wifi driver manually"
date: 2015-11-18
forum: Networking &amp; Wireless
---

### Post by ricardo43 on 2015-11-18
Hi is my first time installing ubuntu. I have installed correctly but i can't connect to internet. 
My ethernet plug never worked, and i can't connect with wireless because i haven't installed the drivers. 
How can i install manually the wifi driver?

---

### Post by Bucky Ball on 2015-11-18
*Thread moved to **Networking and Wireless**.*

Welcome. You need to know which to install first. Have you tried another cable to make sure the problem isn't a faulty cable? Would make your life a lot easier if it was.

Anyway, please open a terminal and copy this in:

```
sudo lshw -C network
```

Hit return and copy/paste the output here between code tags, please (see the last link in my signauture).

(PS: You need control+shift+c and v for copy or paste in a terminal.)

---

### Post by influencedchaos on 2015-11-18
Have you checked to see if your wifi drivers are inside the "Software Sources" application? In Unity you would hit the super key (Windows Key) and in the search type "Software Sources" and inside that application hit "Additional Drivers". This will look to see if it can find any free/proprietary drivers are available and display a list like the attached screenshot.

If your wifi drivers appear there you can simply click the check bubble for it and wait for it to install. Once that is done check your network bar at the top right and see if your wireless network appears.

EDIT: I did realize again that your situation might make it difficult for the automatic detection and installation to work. Did your drivers work inside the Live CD/USB environment as you were installing by any chance? If so it is a very easy thing to fix.


Welcome to Ubuntu, I hope you have a great experience.

---

### Post by Bucky Ball on 2015-11-18
@influencedchaos: Please attached screenshots using Adv Reply and the paperclip icon. Thanks. It also looks like you are using the no longer supported 12.10. Suggest you upgrade to a supported release. 

Also, the user can't connect to the internet so the Additional Drivers option is not an option. You need to be online to install whether there's anything there or not. :)

---

### Post by ricardo43 on 2015-11-19
> **Bucky Ball said:**
> 
Thank you. The erthnet, i think is an hardware problem, when i use windows never worked. This is what says on terminal.
```
  
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
resources: irq:16 memory:de200000-de203fff

*-network DISABLED    
description: Ethernet interface       
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller      
vendor: Realtek Semiconductor Co., Ltd.      
physical id: 0      
bus info: pci@0000:03:00.0       
logical name: eth0    
version: 02       
size: 10Mbit/s       
capacity: 1Gbit/s       
width: 64 bits       
clock: 33MHz       
capabilities:  pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp  mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation       
configuration:  autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI  duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
resources: irq:31 ioport:6000(size=256) memory:d4010000-d4010fff memory:d4000000-d400ffff memory:dd200000-dd20ffff

```

I was thinking if it is possible to install driver manually, by doing download the drive and configure, my self.

---

### Post by ricardo43 on 2015-11-19
> **Bucky Ball said:**
> @influencedchaos: Please attached screenshots  using Adv Reply and the paperclip icon. Thanks. It also looks like you  are using the no longer supported 12.10. Suggest you upgrade to a  supported release. 

Also, the user can't connect to the internet so the Additional Drivers  option is not an option. You need to be online to install whether  there's anything there or not. [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

thank you. i tried that but it dosen't apper anything in there to me

---

### Post by Bucky Ball on 2015-11-19
Try [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access"). From 'b43 - No Internet'. You need to use your install media to get b43 and you need to have a computer online to download some software to transfer to your machine.

As for ethernet, once again, have you tried another cable? If that works it will save you a whole lot of time. It appears to be recognised and have drivers according to your output. It's just disabled.

Come to think of it, have you clicked on the network icon and checked networking is enabled??? 'Enable Networking' should have a tick next to it.

---

### Post by praseodym on 2015-11-19
Alternatively, download this file (somehow) and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 

Installation:
```

sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot. Wireless should work now. After that run:
```

sudo apt-get install build-essential dkms r8168-dkms
```
Reboot. LAN should work now, too.

---

### Post by ricardo43 on 2015-11-19
> **Bucky Ball said:**
> Try [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access"). From 'b43 - No Internet'. You need to use your install media to get b43 and you need to have a computer online to download some software to transfer to your machine.

As for ethernet, once again, have you tried another cable? If that works it will save you a whole lot of time. It appears to be recognised and have drivers according to your output. It's just disabled.

Come to think of it, have you clicked on the network icon and checked networking is enabled??? 'Enable Networking' should have a tick next to it.

I changed the cable and it didn't work. It has some hardware problem for shure.
I  did that method from b43 file, it was a little difficult to understand  waht i had to do, but i made it and now I have wireless :D, and uptdated  the system. 
Thank you very much!

---

### Post by ricardo43 on 2015-11-19
> **praseodym said:**
> Alternatively, download this file (somehow) and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 

Installation:
```

sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot. Wireless should work now. After that run:
```

sudo apt-get install build-essential dkms r8168-dkms
```
Reboot. LAN should work now, too.

I already did the way that Bucky Ball told me, and i managed to get it work, it was a little difficult for me to understand because it's my first time working with this. Your way seems simpler but thank's anyway for the concern.

---

### Post by Bucky Ball on 2015-11-19
Excellent news! Yes, praseodym has way more skills than I do with wifi and their way is easier, but at least it's working now and well done for getting through the instructions.

Could you mark this thread as solved, please (see the first link in my signature, this doesn't close the thread to further discussion, just helps others) and don't hesitate to post a new thread for any further issues. Good luck. :)

---

