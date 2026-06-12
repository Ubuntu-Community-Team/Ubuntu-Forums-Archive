---
title: "Need help with wireless on laptop"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by Philliesfan251 on 2009-06-01
[FONT=Verdana][SIZE=2]I've been looking through posts and have been Google searching and I still can't find the solution. I can't go on the Internet with my Dell Inspiron 1521 Laptop using Ubuntu 9.04. I can connect to unsecure networks but can't surf the web, and I can't connect to my home network at all. I can connect via Ethernet. I activated the Broadcom driver but it didn't work. I've been reading posts and think this will help. 
[/SIZE][/FONT]```
    [FONT=Verdana][SIZE=2]frank@ubuntu:~$ uname -rm[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]2.6.28-11-generic x86_64[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]frank@ubuntu:~$ lspci[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:14.1 IDE interface: ATI Technologies Inc SB600 IDE[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series][/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]frank@ubuntu:~$ lshw -C Network[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]WARNING: you should run this program as super-user.[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]  *-network               [/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       description: Wireless interface[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       product: BCM4311 802.11b/g WLAN[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       vendor: Broadcom Corporation[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       physical id: 0[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       bus info: pci@0000:0b:00.0[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       logical name: eth1[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       version: 01[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       serial: 00:1e:4c:29:a9:77[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       width: 32 bits[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       clock: 33MHz[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       capabilities: bus_master cap_list ethernet physical wireless[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=192.168.0.104 latency=0 module=wl multicast=yes wireless=IEEE 802.11[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]  *-network[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       description: Ethernet interface[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       product: BCM4401-B0 100Base-TX[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       vendor: Broadcom Corporation[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       physical id: 0[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       bus info: pci@0000:03:00.0[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       logical name: eth0[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       version: 02[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       serial: 00:1c:23:ab:f4:56[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       width: 32 bits[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       clock: 33MHz[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       capabilities: bus_master cap_list ethernet physical[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]  *-network DISABLED[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       description: Ethernet interface[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       physical id: 1[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       logical name: pan0[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       serial: a6:a5:a7:81:cc:ed[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       capabilities: ethernet physical[/SIZE][/FONT]
    [FONT=Verdana][SIZE=2]       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/SIZE][/FONT]
    
```[FONT=Verdana][SIZE=2]
I'm an Ubuntu noob. Let me know if you need any more info. 
[/SIZE][/FONT]

---

### Post by mapes12 on 2009-06-02
There appears to be a large amount of posts regarding poor wifi support in 9.04. A fresh install of 8.10 or 8.04 may solve the problem. Alternatively, here are some links that may be helpful:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

[http://madwifi.org/](http://madwifi.org/)

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

[https://help.ubuntu.com/community/Wi...3d3c3468508d45](https://help.ubuntu.com/community/Wi...3d3c3468508d45)

[https://help.ubuntu.com/community/Wi...eShootingGuide](https://help.ubuntu.com/community/Wi...eShootingGuide)

Also, try the Dell Ubuntu forum: [http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

Mark

---

### Post by dwouters on 2009-06-02
> **mapes12 said:**
> There appears to be a large amount of posts regarding poor wifi support in 9.04. A fresh install of 8.10 or 8.04 may solve the problem. Alternatively, here are some links that may be helpful:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

[http://madwifi.org/](http://madwifi.org/)

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

[https://help.ubuntu.com/community/Wi...3d3c3468508d45](https://help.ubuntu.com/community/Wi...3d3c3468508d45)

[https://help.ubuntu.com/community/Wi...eShootingGuide](https://help.ubuntu.com/community/Wi...eShootingGuide)

Also, try the Dell Ubuntu forum: [http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

Mark

Alternatively, you can go here: [http://linux.dell.com/wiki/index.php/Ubuntu_9.04](http://linux.dell.com/wiki/index.php/Ubuntu_9.04) and download the proper ISO directly from Dell for your laptop.

---

### Post by richg on 2009-06-02
Another possibility is, you could install Mint 7 which I think is based on Ubuntu 9.04. I have a Acer Aspire laptop that I installed Mint 7 on and the wireless works right out of the box.
My desktop PC has wireless with Mint 7 and no issues.

Rich

---

