---
title: "[SOLVED] Enable Wireless Card"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by measekite on 2007-10-09
Is there a way to enable a wirelss card so it shows up when you use the GUI System>Administration>Network?

When I issued lshw -C network it showed the name of the card but that it was disabled.

---

### Post by kevdog on 2007-10-09
Is there a driver associated in the lshw output??  Can you post the output.

---

### Post by measekite on 2007-10-09
> **kevdog said:**
> Is there a driver associated in the lshw output??  Can you post the output.

What should I look for?  I have a Linksys wmp11 version one with an Intersel Prism2.5 chipset.

I installed ndiswrapper 1.38.  When 

```
ndiswrapper -v
```

I get some error about ndis util but all of the ndiswrapper commands work.

Let me know what information you need to help me.  I have spent hours on this and no cigar yet.  There are posting that say that this card should work in Linux.  If those postings are erroneous them maybe you could suggest a few cards that will work natively out of the box and hopefully supported by the mfg.

Thanks for your interest.

---

### Post by kevdog on 2007-10-09
Should look something like this

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

Notice the driver=ndiswrapper statement toward the bottom

---

### Post by measekite on 2007-10-11
> **kevdog said:**
> Should look something like this

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

Notice the driver=ndiswrapper statement toward the bottom

Sorry I took so long but I needed access to the PC with the wireless card and then had to transfer the info to my PC via floppy.  Using Feisty

[COLOR=Blue]Here is the information you had indicated you needed to help me.[/COLOR] 

```
~$ **ndiswrapper -v**
[COLOR=Red]utils Error: no version specified![/COLOR]
driver version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 586 

``````
~$ **lspci -nn**
00:00.0 Host bridge [0600]: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub [8086:1130] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82815 815 Chipset AGP Bridge [8086:1131] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 01)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 [8086:244b] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus [8086:2443] (rev 01)
01:00.0 VGA compatible controller [0300]: Matrox Graphics, Inc. MGA G400/G450 [102b:0525] (rev 82)
[COLOR=Red]02:0b.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)[/COLOR]

``````
~$ **lshw**
WARNING: you should run this program as super-user.
mymachine              
          [COLOR=Red] *-network DISABLED[/COLOR]
                description: Ethernet interface
                product: **Prism 2.5 Wavelan chipse**t
                vendor: **Intersil** Corporation
                physical id: b
                bus info: pci@02:0b.0
                logical name: **wlan0**
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes **driver=prism2_pci** latency=32 multicast=yes
                resources: iomemory:f5000000-f5000fff irq:9
```
         
        

          
```
~$ **lsmod | grep host**
hostap_pci             56848  0 
hostap                113924  1 hostap_pci
ieee80211_crypt         7040  1 hostap


``````
~$ **lshw -C network**
WARNING: you should run this program as super-user.
[COLOR=Red]  *-network DISABLED [/COLOR]     
       description: Ethernet interface
       product: **Prism 2.5 Wavelan chipset**
       vendor: **Intersil** Corporation
       physical id: b
       bus info: pci@02:0b.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes **driver=prism2_pci **latency=32 multicast=yes
       resources: iomemory:f5000000-f5000fff irq:9
```Anything you or any other reader can do to help.  I am new to Linux.  I have a couple of weeks experience and have never used a C compiler before.  First and foremost I would like to get this working.  Then I would like to understand what is going on.

I have installed and uninstalled ndiswrapper 1.18 and 1.38 and have tried many drivers others have indicated will work.  I also made an attempt to install hostap but may not have done that correctly.  I even tried to use the drivers that came on a CD with the card.  

I also upgraded the firmware to what ever Linksys recommends on their website.

---

### Post by tormod on 2007-10-17
You don't want to use the prism2_pci driver:
> configuration: broadcast=yes driver=prism2_pci latency=32 multicast=yes

Use orinoco or hostap.

---

