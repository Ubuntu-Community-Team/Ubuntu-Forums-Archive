---
title: "Dapper can't see WMP54G ver 4.1 card"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by UphillSkier on 2006-09-11
I am struggling to install my Linksys WMP54G version 4.1 wireless card.  I
have tried to follow [Judgekaster's excellent Howto]("http://www.ubuntuforums.org/showthread.php?t=132980") but bomb out at the first step:  I can't find the card using lshw or lspci.  

```
mullera@happy:/lib/modules/2.6.15-26-386/kernel/drivers/net$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
  <snip>

mullera@happy:~/downloads/RT61_Linux_STA_Drv1.0.4.0/Module$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
0000:00:11.0 ISA bridge: VIA Technologies, Inc.: Unknown device 3287
0000:00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
0000:00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCIE Bridge
0000:00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3344 (rev 01)
0000:02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
0000:02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
0000:02:01.0 0403: VIA Technologies, Inc. VIA High Definition Audio Controller

```

The card works fine under Windows XP, so something is very strange. 
I am running Xubuntu subsequently upgraded to gnome desktop.

```
mullera@happy:~$ cat /proc/version
Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREE MPT Thu Aug 3 02:52:00 UTC 2006

```

Any help would be greatly appreciated.

---

