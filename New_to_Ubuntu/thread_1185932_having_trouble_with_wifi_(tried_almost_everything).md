---
title: "having trouble with wifi (tried almost everything)"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by akamigs on 2009-06-12
Compaq Presario F761US Notebook.

9.04 Ubuntu

Have everything working except for wifi (Atheros card).

I have tried:

# tar xvzf madwifi-0.9.4.tar.gz
# cd madwifi-0.9.4
# make
# make install

And:

wget 'http://snapshots.madwifi-project.org/special/madwifi-ng-r2756+ar5007.tar.gz'
tar zxvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
make clean
make
make install
reboot
ifconfig ath0 up

Nothing happens. Help please. Thank you.

lspci:

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by ptn107 on 2009-06-12
Try a backported version of the driver:
```
sudo aptitude install linux-backports-modules-jaunty
```

---

### Post by akamigs on 2009-06-12
> **ptn107 said:**
> Try a backported version of the driver:
```
sudo aptitude install linux-backports-modules-jaunty
```

still no luck :(

---

### Post by drkameleon on 2009-06-12
Hi akamigs,

I would suggest a very... alternative solution but it has worked indeed for me lots of times.

**1) **Go to System->Administration->Synaptic Package Manager

**2) **Search for 'ndiswrapper', select EVERYTHING (that appears as a result) and install them.
[B]
3) [/B]Find a VALID Windows Driver for your wireless card and unzip it.

**4) **Open System->Administration->Windows Wireless Drivers (that's the "NDISWRAPPER" you installed earlier). ADD another driver by POINTING Ndiswrapper to the .INF file of your Windows Driver (Browse it)

**5) **Reboot.

If you still have any problem, please let me know... ;)

Dr.Kameleon

---

### Post by drkameleon on 2009-06-12
(* By the way, I am ALSO an Atheros-card owner... AR5005G)

**Another possible solution (if the above one fails)**
, would be to go to System->Administration->Hardware Drivers and try enabling the "Alternate" driver suggested. 

Then reboot. If you still don't see anything after the reboot, try a...

```
sudo modprobe ath5k
```

Cheers!

---

### Post by akamigs on 2009-06-12
> **drkameleon said:**
> Hi akamigs,

I would suggest a very... alternative solution but it has worked indeed for me lots of times.

**1) **Go to System->Administration->Synaptic Package Manager

**2) **Search for 'ndiswrapper', select EVERYTHING (that appears as a result) and install them.
[B]
3) [/B]Find a VALID Windows Driver for your wireless card and unzip it.

**4) **Open System->Administration->Windows Wireless Drivers (that's the "NDISWRAPPER" you installed earlier). ADD another driver by POINTING Ndiswrapper to the .INF file of your Windows Driver (Browse it)

**5) **Reboot.

If you still have any problem, please let me know... ;)

Dr.Kameleon

unfortunately this one gives me an error: "unable to see if hardware is present"

let me try your next suggestion. THANK YOU BTW.

---

### Post by akamigs on 2009-06-12
> **drkameleon said:**
> (* By the way, I am ALSO an Atheros-card owner... AR5005G)

**Another possible solution (if the above one fails)**
, would be to go to System->Administration->Hardware Drivers and try enabling the "Alternate" driver suggested. 

Then reboot. If you still don't see anything after the reboot, try a...

```
sudo modprobe ath5k
```

Cheers!

The first part of this suggestion was my very 1st attempt.

HOWEVER, the code you provided WORKED. I HAVE WIFI. THANK YOU VERY MUCH SIR!!! :)

---

### Post by drkameleon on 2009-06-12
> **akamigs said:**
> unfortunately this one gives me an error: "unable to see if hardware is present"

let me try your next suggestion. THANK YOU BTW.

Well, I've encountered this "unable..." thing myself as well. How about finding ALTERNATIVE versions of the Win Driver? (that had once helped me...)

[*** A very good resource for Atheros Drivers ***]("http://www.atheros.cz")

---

### Post by drkameleon on 2009-06-12
> **akamigs said:**
> The first part of this suggestion was my very 1st attempt.

HOWEVER, the code you provided WORKED. I HAVE WIFI. THANK YOU VERY MUCH SIR!!! :)

I'm HAPPY to hear that. I've been struggling myself with my Atheros Wireless Card for such a long time, and I DO KNOW what a pain it is not to be able to get it work.... :)

Cheers! ;)

Dr.Kameleon

---

### Post by drkameleon on 2009-06-12
Another important thing which btw I asked myself before,

if you don't want to type every single time you boot that "sudo modprobe ath5k"...

just type in the terminal

```
sudo gedit /etc/modules
```

Add at end of the "/etc/modules" file the line

```
ath5k
```

Save the file and reboot.

---

### Post by akamigs on 2009-06-12
> **drkameleon said:**
> Another important thing which btw I asked myself before,

if you don't want to type every single time you boot that "sudo modprobe ath5k"...

just type in the terminal

```
sudo gedit /etc/modules
```

Add at end of the "/etc/modules" file the line

```
ath5k
```

Save the file and reboot.

Where do I insert 'ath5k' ?

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

---

