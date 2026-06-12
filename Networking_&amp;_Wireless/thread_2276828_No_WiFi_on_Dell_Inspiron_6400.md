---
title: "No WiFi on Dell Inspiron 6400"
date: 2015-05-05
forum: Networking &amp; Wireless
---

### Post by pintosal on 2015-05-05
I have just installed Ubuntu on my Dell Inspiron 6400 laptop, dual booting with Windows XP.

While the ethernet connection works fine, the WiFi does not work at all. Under XP the WiFi works perfectly.

I'm new to Ubuntu, so I am stuck, and I would welcome some help to get this working.

---

### Post by roger_1960 on 2015-05-05
Hi

Could you open a terminal CTR+ALT+T

run these 2 commands one at a time

> lspci -nn
sudo lshw -C network

and post the results back.  That should identify your wifi hardware.

Also, try shutting down/power off.  Restart into windows. Make sure the wifi is on when you exit windows and then restart ubuntu.  I have had a situation where the wifi switch only works in windows.

EDIT: Just found this post which may well help you: [http://ubuntuforums.org/showthread.php?t=2220454](http://ubuntuforums.org/showthread.php?t=2220454)

Roger

---

### Post by pintosal on 2015-05-05
```
sp@UBDell:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 01)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
sp@UBDell:~$ 
sp@UBDell:~$ sudo lshw -C network
[sudo] password for sp: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:87:f1:e0
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.117 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff
sp@UBDell:~$ ^C
sp@UBDell:~$
```

Thanks Roger. Hopefully that tells you about my hardware.

Yes, wireless is switched on in Windows.

---

### Post by roger_1960 on 2015-05-05
Hi

That confirms that you probably have the same issue as in the post I found.

Do this in terminal one line at a time.  When it asks for your password type it in - it won't show at all - press return. Wait for each instruction to complete and return to the entry cursor before entering (copy and paste) the next one. (use right click for the copy and paste in terminal)

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```

Then reboot - hopefully that should work

Roger

---

### Post by pintosal on 2015-05-05
Tried that. Is the message [COLOR=#0000cd]*Package 'bcmwl-kernel-source' is not installed, so not removed*[/COLOR] significant?

```
sp@UBDell:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for sp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 217 not to upgrade.
sp@UBDell:~$
```


Then

```
sp@UBDell:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 217 not to upgrade.
sp@UBDell:~$
```

However, still no WiFi

---

### Post by slickymaster on 2015-05-05
*Moved to the ***Networking & Wireless*** sub-forum*

@pintosal:
I've edited a couple of your posts, adding code tags to them. Output code, posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by pintosal on 2015-05-05
Thanks @slickymaster. My apologies and I'll do that in future.

---

### Post by roger_1960 on 2015-05-05
Hi again

Well then, try this

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

and reboot

Roger

---

### Post by pintosal on 2015-05-05
You are a star Roger - thanks!!!

WiFi and ethernet are now working, and this post was made using WiFi.

As I'm a novice, I slavishly followed your commands. Could you explain what the problem was and how it was resolved?

---

### Post by roger_1960 on 2015-05-05
Hi

Your install could have been using the bcmwl drivers for your broadcom 4311 hardware.  (Actually its a good idea to state which ubuntu you are using when you post) We first tried to uninstall that and reinstall in case there was an issue with the install.  It was not present - you asked about that.  The alternative and newer drivers have worked.  They are available in the ubuntu repositories in current versions of ubuntu and we have installed them.  I'm not totally familiar with broadcom problems (which have persisted for many years) - if I had been a broadcom user I would probably have solved it quicker!  :)

Anyway, welcome to these forums - don't hesitate to ask if you have issues.  Do Use the search facilities before posting, there really is a lot of info available.

Don't forget to marked the thread as solved!

Roger

---

### Post by edge3 on 2016-01-24
[**[COLOR=#000000]roger_1960[/COLOR]**]("http://ubuntuforums.org/member.php?u=430600") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]

th&#1100; a lot for your help )))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))

---

