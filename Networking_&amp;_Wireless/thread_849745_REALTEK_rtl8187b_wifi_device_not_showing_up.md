---
title: "REALTEK rtl8187b wifi device not showing up"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by LifeTheHound on 2008-07-04
I tried downloading the official windows driver and using ndiswrapper, and it recognizes and installs correctly.

But no wlan settings show up in network manager!  Ubuntu *still doesn't know my Gateway has wifi*, and **won't even show any wireless interface as being installed**.  

What do I need to do?

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:f9:53:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:250 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:0f:b3:58:6d:cf  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b3ff:fe58:6dcf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8353 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17979261 (17.1 MB)  TX bytes:1182643 (1.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11000 (10.7 KB)  TX bytes:11000 (10.7 KB)
```
iwconfig says:
```
linda@lindalinux:~/Desktop/ndiswrapper-1.53$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

```
lspci says:
```

linda@lindalinux:~/Desktop/ndiswrapper-1.53$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

```
Running Ubuntu 8.04.1, **[color=red]64-bit edition[/color]**.

---

### Post by mbarvian on 2008-07-05
I have the exact same wireless card as you.  I solved it using the first section on this post:

[https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide](https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide)

Hope this helps!

---

### Post by LifeTheHound on 2008-07-06
It did get the card recognized, and with the tweaks he mentions, I got it to apply at startup.  It will actually connect to unsecure networks most of the time, but it completely crashes the system when I try to connect to my home (WEP-open) network.  The entire system locks completely and won't respond to anything at all, even mouse movement.  

Is there any way around this obstacle?  Thanks again!

---

### Post by LifeTheHound on 2008-07-07
...it looks like I spoke too soon.  After I canceled out of network validation on my network (so I could remove my password), it won't even connect to my now unsecured network.  My other Ubuntu laptop (a Dell) does fine.  

Or should I just give up on Ubuntu/internet for this particular laptop?

---

### Post by LifeTheHound on 2008-07-07
Look what I found: [http://www.linuxquestions.org/questions/linux-wireless-networking-41/get-your-rtl8187b-working-with-winxp-driver-610613/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/get-your-rtl8187b-working-with-winxp-driver-610613/)

What is this guy saying?  I did what he said but have no idea where to go from here.  Any ideas?  Do I use this inf with ndiswrapper or something?  And if I do, the network should magically appear?

---

### Post by lrbradford on 2008-07-14
I followed the instructions from the Ubuntu forum:

[https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide](https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide)

It did get me the wireless to show up finally in Network Manager, but I could not connect to my wireless router which has security WPA2 Personal.  I need to add the command to load the wlan0up on startup, but I doubt if this is going to solve my wireless woes.

LB

---

### Post by onewithnature83 on 2008-07-20
Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---

