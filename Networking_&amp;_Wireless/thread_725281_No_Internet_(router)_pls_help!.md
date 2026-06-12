---
title: "No Internet (router) pls help!"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by ftv00es on 2008-03-15
Hi! 

Well, just bought a router and I can't connect to the internet or contact (ping?) the router. The router works good as in Windows (same PC) works and in a second computer with Kubuntu works fine. 

The router is a Belkin F5D7230-4. 

I tried everything I read in the forums and I just cannot make it work. I even reinstalled Ubuntu (deleting partition and all) and *nada*. To save everyone some time I compiled all the Terminal responses that suppose to help.

```


**/etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

------------
ferran@ferran-desktop:~$** ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:19:21:B2:5D:B4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xac00 

eth0:avah Link encap:Ethernet  HWaddr 00:19:21:B2:5D:B4  
          inet addr:169.254.7.106  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen

-----------------
ferran@ferran-desktop:~$ **route**

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0


-----------
ferran@ferran-desktop:~$ **lspci**

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

-----------------

ferran@ferran-desktop:~$ **lshw -C network**

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:19:21:b2:5d:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

----------
ifup: interface eth0 already configured



```

I think that's all... internet used to work before with and old router, then I switched to direct to modem, and now this new router. That's why I though I must have messed up something. So I reinstall Ubuntu and still doesn't work :(  

Please, if anyone have a suggestion of what might happen, let me know. Thanks in advance to all the Ubuntu knowledgeable people around! :) 

Ferran.

BTW! The connection is set up to DHCP because the router assigns IP's to each computer. So no need to fixed IP (as far as I know :P).  Also, when Windows is working the light on the modem indicating the computer is on is lighted. When I'm in Ubuntu, the light is off, like if there was no computer plugged in!

(Sorry, some code got mixed up while opening a text file in Windows... tell me if you need it again)

---

### Post by ftv00es on 2008-03-15
I finally fixed it connecting to my router through wireless... can't believe it works better than wired connection.... 
Still if anyone has a solution for my wired connection it would be appreciated.

---

### Post by ugm6hr on 2008-03-15
If it works in Windows (dual-boot) - this is the most likely problem:
[http://ubuntuforums.org/showpost.php?p=4077372&postcount=14](http://ubuntuforums.org/showpost.php?p=4077372&postcount=14)

Turn off the relevant power-saving feature in Windows, and it should work fine.

---

### Post by ftv00es on 2008-03-15
Thanks! Just did it and rebooted and still nothing. As I have been messing up with the connections in ubuntu, I think I'll try installing Kubuntu. If it works for the second computer, it must work on this one (cross fingers). Now I'm just going to chill far away of the computer as I spent more than 5 hours with this and I'm starting to get annoyed... It sucks this is so complicated... Thanks anyway!! ;)

---

### Post by ugm6hr on 2008-03-15
If you have turned that power-saving feature off, you can test whether it works from a LiveCD.

That will confirm whether you have edited things that need to be returned to default.

---

### Post by ftv00es on 2008-03-15
When I use the LiveCD I also don't have internet connection. I even tried installing the 7.04 version and still nothing. 
As I have a wireless router I even tried connecting to the internet with a USB dongle thingy and in fact it worked! But just barely. web fine, tried to update or add program and nothing. It's just if linux has decided it doesn't want me online, LOL. It sucks because I liked it and I hate to have to go back to Windows. :( 
Tomorrow I plan in installing Kubuntu (wanted to try it anyway). But my question is: if the LiveCD doesn't connect to the internet, does that mean that even if I install it it won't work?
Thanks!

---

### Post by superprash2003 on 2008-03-16
check this out [http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html](http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html) .. read the ROAMING MODE section

---

