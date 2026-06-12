---
title: "[SOLVED] Both network cards down since upgrade"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by headsign on 2008-11-28
Unfortunately, since the upgrade to Intrepid Ibex, both network cards, one being a Linksys WPC54G (Broadcom 43xx) WiFi card and the other a Netgear FA411 Ethernet card are not recognized anymore.

I spent hours wading through threads and trying to install patches. I am sad and tired. Has anybody got a comprehensive method of getting at least one card to work on this old Ispiron 7000?

Thanks

edit: I forgot to mention that those are PCMCIA cards.

---

### Post by Coreigh on 2008-11-28
Do they (either one) work when you boot from the LiveCD? Xubuntu OR Ubuntu CD.

---

### Post by Ayuthia on 2008-11-28
Can you post the results of:
```
lspci -nn
lshw -C network
```

---

### Post by headsign on 2008-11-29
> **Ayuthia said:**
> Can you post the results of:
```
lspci -nn
lshw -C network
```

Here are the results with the Linksys card inserted. Shall I do the same thing with the Netgear PCMCIA Ethernet controller inside?

By the way: the latter shows network activity, or at least the green "link" LED is blinking during some operations, but it does not seem to be recognized by the system itself.

```

headsign@headsign-ubuntu:~$ sudo lshw -C network
[sudo] password for headsign: 
  *-network               
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 1
       resources: irq:11
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:01:8c:e5:cc:a3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0f:66:97:c2:0d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

...sorry: this part keeps on erasing the "code"-end tag...

headsign@headsign-ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 02)
00:04.0 CardBus bridge [0607]: Texas Instruments PCI1220 [104c:ac17] (rev 02)
00:04.1 CardBus bridge [0607]: Texas Instruments PCI1220 [104c:ac17] (rev 02)
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 02)
00:08.0 Multimedia audio controller [0401]: ESS Technology ES1968 Maestro 2 [125d:1968]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc 3D Rage LT Pro AGP-133 [1002:4c42] (rev dc)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

---

### Post by headsign on 2008-11-29
> **Coreigh said:**
> Do they (either one) work when you boot from the LiveCD? Xubuntu OR Ubuntu CD.

Well first of all I have an Ubuntu 8.04 live CD but no Xubuntu 8.1 live CD. The latter is alternate and offers no live session.
I tried the Ubuntu 8.04 live CD. Result: for the Lynsys WPC54G card, it offers to install a proprietary driver via fwcutter, which is a Broadcom 43 driver but is unable to perform this installation due to not being connected to the internet.
The Netgear FA411 card works "right out of the box" from the live CD.

---

### Post by Ayuthia on 2008-11-29
> **headsign said:**
> Well first of all I have an Ubuntu 8.04 live CD but no Xubuntu 8.1 live CD. The latter is alternate and offers no live session.
I tried the Ubuntu 8.04 live CD. Result: for the Lynsys WPC54G card, it offers to install a proprietary driver via fwcutter, which is a Broadcom 43 driver but is unable to perform this installation due to not being connected to the internet.
The Netgear FA411 card works "right out of the box" from the live CD.

The only thing that I can provide for your Linksys card is this [link]("http://ubuntuforums.org/showpost.php?p=6028741&postcount=4").  It has the instructions on what you need to download so that you can install it in Ubuntu.

As for the Netgear card, if you use the live CD, can you still use the card out of the box?  If so, please go into the Terminal and check:
```
lshw -C network
```so that you can see what driver it is using.  There is a chance that the driver is not loaded after the install.  That is my guess.  If you are not for sure about how to load/unload a driver, please post the results of lshw -C network from the live CD.

---

### Post by headsign on 2008-11-30
It works (the broadcom card)! :) Many thanks to you, Ayuthia.

I will try to fix the Netgear card later today.

---

### Post by headsign on 2008-12-03
One last question (for now): how do I get Xubuntu to activate the driver automatically after a reboot?

---

### Post by Ayuthia on 2008-12-03
I am not for sure if I fully understand the question.  If you are saying that the b43 driver is not loading when the system boots up:
```
echo b43 | sudo tee -a /etc/modules
```Should add the module for you.  However, you will want to check and see if the b43 module is currently blacklisted:
```
cat /etc/modprobe.d/blacklist|grep b43
```If it returns:
```
blacklist b43
```then you will need to remove it or comment it out:
```
gksu gedit /etc/modprobe.d/blacklist
```I am not for sure if gksu or gedit are applications in Xubuntu or not so if it isn't just use your favorite editor in sudo mode so that you can update the file.  If you want to comment out the line instead of deleting the line, make the line look like:
```
#blacklist b43
```

If you are just wanting to have it connect to a particular site, I am not an expert on this one.  I tend to do things manually.  I am also not too familiar with Xubuntu so I am not for sure if it has some kind of network manager equivalent or not, but it should be able to automatically connect for you.  If it does not, here is a link that might help:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
This is kevdog's guide for manual connections.  At the end he has a way to have your system connect to a particular access point at boot. 

Hope that helps.

---

### Post by headsign on 2008-12-05
Thank you. Sorry for being misunderstandable. It was indeed blacklisted. This must have happened while previously experimenting with several recipies on how to make the Wifi card work.

---

