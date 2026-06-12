---
title: "Wireless not found on Acer Aspire One AOA150"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by needledreams on 2010-04-27
I installed Ubuntu in my netbook Acer Aspire One AOA150 and haven't been able to enable the wireless.  Neither the card reader for my SD cards (it has 2 slots).

I'm completely new in this.  Installed Ubuntu becausea friend recommended it, I try it and like it, but now I can't connect to internet to get my backups and install my programs.

When I installed Ubuntu I made the "mistake" of format the hard drive to install only Ubuntu.  :(

HELP!!!  ](*,)

---

### Post by bumanie on 2010-04-27
Go to terminal and post the output of > lspciThat will show what wireless card you have (+ a lot more) and then someone can help, once they which card/chipset it is.

---

### Post by bodhi.zazen on 2010-04-27
> **needledreams said:**
> I installed Ubuntu in my netbook Acer Aspire One AOA150 and haven't been able to enable the wireless.  Neither the card reader for my SD cards (it has 2 slots).

I'm completely new in this.  Installed Ubuntu becausea friend recommended it, I try it and like it, but now I can't connect to internet to get my backups and install my programs.

When I installed Ubuntu I made the "mistake" of format the hard drive to install only Ubuntu.  :(

HELP!!!  ](*,)

What version of Ubuntu did you install ?

I have used the same netbook with Karmic (ubuntu 9.10) , wireless worked flawlessly with Xubuntu and the UNR edition.

---

### Post by needledreams on 2010-04-27
wally@wally-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)

---

### Post by needledreams on 2010-04-27
> **bodhi.zazen said:**
> What version of Ubuntu did you install ?

I have used the same netbook with Karmic (ubuntu 9.10) , wireless worked flawlessly with Xubuntu and the UNR edition.

I installed ubuntu 9.10.  Even dowloaded the drivers from Acer page but I can't install them.  An error window opens each time I wangt to install anything.

---

### Post by anewguy on 2010-04-27
I didn't see the wireless while looking at your lspci output, so please do the following and post the outputs back here:

lsusb

lshw -C network


Thanks
Dave ;)

---

### Post by needledreams on 2010-04-27
> **anewguy said:**
> I didn't see the wireless while looking at your lspci output, so please do the following and post the outputs back here:

lsusb

lshw -C network


wally@wally-laptop:~$ lsusb 
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
wally@wally-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:23:8b:83:e3:bb 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list rom ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes 
       resources: irq:28 ioport:3000(size=256) memory:51010000-51010fff(prefetchable) memory:51000000-5100ffff(prefetchable) memory:51020000-5103ffff(prefetchable) 
  *-network DISABLED 
       description: Wireless interface

---

### Post by anewguy on 2010-04-27
Wasn't there more output after the ending lines:

> *-network DISABLED
description: Wireless interface

All that did was let us know there is apparently a wireless interface ( I still haven't seen it in the lists).  Please post the remainder (it probably scrolled) of that output.

I'm also wondering if you posted all of the output from lspci, as the lsusb doesn't show a wireless device so it must be pci, so I assume it scrolled beyond what you posted.  Please post the complete output of that as well.

Dave ;)

---

### Post by needledreams on 2010-04-27
I think I got it all now.  Sorry it was incomplete before.



wally@wally-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) 
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01) 
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller 
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller 
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller 
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller 
wally@wally-laptop:~$ lsusb 
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
wally@wally-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:23:8b:83:e3:bb 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list rom ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes 
       resources: irq:28 ioport:3000(size=256) memory:51010000-51010fff(prefetchable) memory:51000000-5100ffff(prefetchable) memory:51020000-5103ffff(prefetchable) 
  *-network DISABLED 
       description: Wireless interface 
       product: AR5001 Wireless Network Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wmaster0 
       version: 01 
       serial: 00:24:2b:b4:db:d1 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg 
       resources: irq:18 memory:55200000-5520ffff

---

### Post by anewguy on 2010-04-28
Okay, we can see now that your wireless is:  

> description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.


So we know you need a driver for the AR5001.  I'm sure you can probably find that here just putting ar5001 driver in the search on this forum.  I don't know if it works with this chipset or not, but you could try:

- temporarily hard-wire your netbook to a router

- sudo apt-get update

- check under System/Administration/Hardware Drivers and see if a driver shows -> if so, enable it

- disconnect your hard-wire cable

- check network manager to see if you have wireless networks now


Additionally, I'm curious if you have thought about just installing the unr (Ubuntu Netbook Remix, I think) version as per bodhi.zazen, since the wireless will apparently work out of the box with that.

Dave ;)

---

### Post by Silver40mm on 2010-04-28
I would definitely try hard-wiring to your router first and updating via Synaptic, if you have a spare cable. It's usually what works for me when that happens.

---

### Post by needledreams on 2010-04-28
I wired the computer and it won't connect to the internet anyway.  It says Network Disabled, but I can't find where to enable it.

I'm reinstalling Ubuntu the Netbook Remix to see if it works.

Same problem....


I downloaded the driver from [http://www.atheros.cz/getfile.php](http://www.atheros.cz/getfile.php) as a zip but I don't know how to install it.  Where should I extract it?

I'm getting anxious because in a couple of days I have an art exhibition and I use the computer for it.

---

### Post by LewRockwell on 2010-04-28
let us know how it works out for you and if you need more assistance it might help us to know the complete model numbers and version numbers of your netbook and any network devices such as routers and modems.

.

---

### Post by needledreams on 2010-04-28
I installed the UNR.  Installed ndiswrapper.  It connected to the internet (wired) and made an upgrade.  Then I restarted the computer as indicated after the upgrade.  Now it won't connect again to the internet (wired). I ran again the previous steps and this is what it says:

wally@wally-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) 
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01) 
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller 
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller 
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller 
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller 
wally@wally-laptop:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
wally@wally-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network UNCLAIMED     
       description: Ethernet controller 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 02 
       width: 64 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=0 
       resources: ioport:3000(size=256) memory:51010000-51010fff(prefetchable) memory:51000000-5100ffff(prefetchable) memory:51020000-5103ffff(prefetchable) 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR5001 Wireless Network Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 
       resources: memory:55200000-5520ffff 
wally@wally-laptop:~$

---

### Post by LewRockwell on 2010-04-28
What is the output of:```
sudo ifconfig -a
```

---

### Post by needledreams on 2010-04-28
> **LewRockwell said:**
> What is the output of:```
sudo ifconfig -a
```

wally@wally-laptop:~$ sudo ifconfig -a 
[sudo] password for wally: 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B) 

wally@wally-laptop:~$

---

### Post by LewRockwell on 2010-04-28
[http://ubuntuforums.org/showthread.php?t=1305812](http://ubuntuforums.org/showthread.php?t=1305812)

---

### Post by LewRockwell on 2010-04-28
If that particular thread doesn't help you then there are quite a few others that you will find via a search for AR5001

.

---

### Post by needledreams on 2010-04-28
> **LewRockwell said:**
> If that particular thread doesn't help you then there are quite a few others that you will find via a search for AR5001

.

After doing so many things I think I got it.  \\:D/  I got madwifi and installed or ran it thru Terminal, blacklisted the ath and then I ran the code
```
sudo modprobe ath5k
```

After this, magically, the computer recognized the wifis in the area.

I hope this last!  Thanks for all the help!  Now to try to upload my hard drive backup.

---

