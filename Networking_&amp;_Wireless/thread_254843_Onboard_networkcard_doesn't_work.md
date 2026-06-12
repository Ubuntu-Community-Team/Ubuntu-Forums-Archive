---
title: "Onboard networkcard doesn't work"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by phreaky- on 2006-09-10
Hello,

**Summary:** 'How do I get my onboard NIC to work again?'

I bought myself a Intel Pro 1000GT NIC. Put it into my system and turned off the onboard NIC in the bios. (mistake i found out) I installed Ubuntu 6.06 server (shell only) and it works great. Uptime: 55 days. 

Now comes the problem. I need the onboard NIC again for LAN purposes. So I turned it back on in the bios. But no go :( I'm used to Windows which will detect it automatically again. But that didn't happen.

So how dow I solve this problem? Can someone point me in the right direction. I have a Asrock k741GX motherboard. [http://www.asrock.com/PRODUCT/K7S41GX.htm](http://www.asrock.com/PRODUCT/K7S41GX.htm). Not much info about the NIC  though. But I installed Ubuntu before with the NIC turned on in the bios and it detected it fine. 

Basicly i don't know much about solving hardware related problems. So your help would be appreciated. And ofcourse I want to learn more. Good linux documents related to this are welcome to :)

---

### Post by doducchinh86 on 2006-09-11
Don't worry! It usually happen to ubuntu because the new mobo. You should find (borrow) a network card (3com or linkpro) and use it. All the problem will be solved:D

---

### Post by amo-ej1 on 2006-09-11
Well it's highly probable that the module isn't loaded yet. Could you providue us with the output of 
```

lspci 

```

When we know how the NIC gets called there it's rather easy to identify the type and the module that needs to be loaded.

---

### Post by amo-ej1 on 2006-09-11
[http://www.asrock.com/support/download.asp?Model=K7S41GX](http://www.asrock.com/support/download.asp?Model=K7S41GX) states:

```

SiS PCI Fast Ethernet Adapter Driver Version:1.16b

```

Just guessing here, open a  console and type

```

sudo modprobe sis190
sudo modprobe sis900

```

And provide us with the last 10 lines of the output of 'dmesg'. It would be my guess that one of the two modules should be able to detect the onboard NIC. Once you find out which one it's only a matter of making the loading of the module persistent.

---

### Post by phreaky- on 2006-09-11
**LSPCI gives the following output:**

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:09.0 Mass storage controller: Promise Technology, Inc. PDC20718 (SATA 300 TX4) (rev 02)
0000:00:0a.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter

**DMESG**

[42949395.140000] kjournald starting.  Commit interval 5 seconds
[42949395.140000] EXT3 FS on sdd1, internal journal
[42949395.140000] EXT3-fs: mounted filesystem with ordered data mode.
[42949405.710000] eth0: no IPv6 routers present
[43650493.890000] e1000: eth0: e1000_watchdog_task: NIC Link is Down
[43650496.400000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
[44943855.430000] e1000: eth0: e1000_watchdog_task: NIC Link is Down
[44943868.840000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
[46039582.520000] e1000: eth0: e1000_watchdog_task: NIC Link is Down
[46039586.160000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex

sudo modprobe sis900 doesn't do anything. Maybe I don't have the driver at all? And driver suggested above looks like a Windows driver to me

---

### Post by kipeloff on 2006-09-12
Hello.

I have the same issue as you, I've battled with on-board NIC and 6.06 release. Ubuntu is installed on different workstation (even with on-board NIC), they work very fine. 

I've decided to install 6.06 from the scratch to one workstation, that has built-in 1Gbps NIC (information about mottherboard [http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1939]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1939")).
Installation ended successfully, but on-board card doesn't work correctly.
Interface was shown in 'Networking', it was possible to set IP configuration.
But interface doesn't work:
- ifconfig was showing correct information;
- route didn't show default gateway (only dynamic entry for configured IP address);
- arp didn't resolve correctly ARP information from gateway;
- /etc/network/interfaces showed correct information;
- only dmesg ethX showed, that 'sd' driver needs update.

I have searched in the forum and find that it is very common problem, that freshly installed 6.06.
3 most common advices were:
- To add entry to /etc/hosts file (it doesn't help to resolve my issue);
- To disable IPv6 support (I don't know how it should help:cool: );
- To find another Ethernet card and try this one.

The last statement resolved my issue, I've plugged another Ethernet card. Installed all updates, and wola :biggrin: on-board card started to work.

---

