---
title: "Internet connection keeps dropping out."
date: 2009-10-12
forum: New to Ubuntu
---

### Post by fixerman on 2009-10-12
I have a problem with my wireless internet access dropping out after varying periods from 10 seconds to an 15 minutes. When it drops out it does no come back unless I disconnect the wireless connection and reconnect. The wireless indicator on the top panel does not change after dropping out but continues to show 80% signal strength. Wired connection is perfect.

I googled this problem and it seems that it was a known problem in previous versions but should not occur in 9.04.

Please help because if I cannot resolve this issue I will have to reinstall windows and I don't really want to do that.

---

### Post by cariboo on 2009-10-12
It would be a lot easier to help with your problem if we had more information. Please paste the output of the following two commands in your next post.

```
lspci
```

and

```
sudo lshw -C network
```

---

### Post by lidex on 2009-10-12
Can you give details of the problem? System details, software , hardware, 64 or 32 bit, laptop??

---

### Post by fixerman on 2009-10-12
> **cariboo907 said:**
> It would be a lot easier to help with your problem if we had more information. Please paste the output of the following two commands in your next post.

```
lspci
```and

```
sudo lshw -C network
```

fixerman@fixerman-laptop:~$ 
fixerman@fixerman-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
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
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
fixerman@fixerman-laptop:~$

---

### Post by fixerman on 2009-10-12
> **cariboo907 said:**
> It would be a lot easier to help with your problem if we had more information. Please paste the output of the following two commands in your next post.

```
lspci
```and

```
sudo lshw -C network
```


fixerman@fixerman-laptop:~$ sudo lshw -C network
[sudo] password for fixerman: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:60:8e:14
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5787m-v3.13 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:d8:51:78
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.5 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:d2:25:c1:20:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
fixerman@fixerman-laptop:~$

---

### Post by sandyd on 2009-10-12
```
    
fixerman@fixerman-laptop:~$ sudo lshw -C network
[sudo] password for fixerman: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:60:8e:14
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5787m-v3.13 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       **logical name: wmaster0**
       version: 02
       serial: 00:18:de:d8:51:78
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.5 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:d2:25:c1:20:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
fixerman@fixerman-laptop:~$
```the bolded part already shows a problem.
having wmaster0 instead of wlan0 indicates some kind of compatibility problem.
EDIT:
and i was right.

see here.[http://ubuntuforums.org/showthread.php?t=1216518](http://ubuntuforums.org/showthread.php?t=1216518)
you need to download the driver from intel manually.

---

### Post by fixerman on 2009-10-13
Thanks Carlee,

Is there no easy way for a novice like me to download this driver. I thought that Linux was going to be easy. All this DOS type stuff is way over my head I'm afraid.

---

### Post by lidex on 2009-10-13
Try this. Go to your main menu "System>Administration>Software Sources". On the "Ubuntu Software" tab make sure all five boxes are checked. Click the "Updates" tab. Under "Ubuntu Updates" are four boxes. Check 'em all. Click the "Close" button and allow it to refresh the repositories.

Now open a terminal and enter these commands one line at a time and allow each to run it's course:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-backports-modules-jaunty
```

When finished, reboot.

---

### Post by fixerman on 2009-10-13
> **lidex said:**
> Try this. Go to your main menu "System>Administration>Software Sources". On the "Ubuntu Software" tab make sure all five boxes are checked. Click the "Updates" tab. Under "Ubuntu Updates" are four boxes. Check 'em all. Click the "Close" button and allow it to refresh the repositories.

Now open a terminal and enter these commands one line at a time and allow each to run it's course:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-backports-modules-jaunty
```

When finished, reboot.

Thank you for your very clear and precise instructions. I have carried them out and rebooted. I am connected wirelessly now so lets see how long it will last.

Of course I have no idea what I was doing. Just a leap of faith I guess.

Thanks again.

---

### Post by fixerman on 2009-10-14
> **lidex said:**
> Try this. Go to your main menu "System>Administration>Software Sources". On the "Ubuntu Software" tab make sure all five boxes are checked. Click the "Updates" tab. Under "Ubuntu Updates" are four boxes. Check 'em all. Click the "Close" button and allow it to refresh the repositories.

Now open a terminal and enter these commands one line at a time and allow each to run it's course:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-backports-modules-jaunty
```When finished, reboot.


Thanks lidex! All seems to be well now. Well done!

---

### Post by Mark201 on 2009-10-30
> **carlee said:**
> ```
    
fixerman@fixerman-laptop:~$ sudo lshw -C network
[sudo] password for fixerman: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:60:8e:14
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5787m-v3.13 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       **logical name: wmaster0**
       version: 02
       serial: 00:18:de:d8:51:78
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.5 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:d2:25:c1:20:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
fixerman@fixerman-laptop:~$
```the bolded part already shows a problem.
having wmaster0 instead of wlan0 indicates some kind of compatibility problem.
EDIT:
and i was right.

see here.[http://ubuntuforums.org/showthread.php?t=1216518](http://ubuntuforums.org/showthread.php?t=1216518)
you need to download the driver from intel manually.

I was having similar problems and followed the instructions, and I checked again and instead of having wmaster0 now I have pan0. Is that right? 

(Usually my internet keeps disconnecting from my college wifi, but not my wifi at home... it's not a problem with the college wifi because the connection is fine with windows.)

---

### Post by teklife on 2012-12-16
i have been having this same problem for months(using 12.04), but it's getting too annoying to ignore now, can anyone tell me what's wrong with my wireless? 

here's the output from terminal:

ss@ss-LinuxBookPro:~$ **lspci**
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation G84 [GeForce 8600M GT] (rev a1)
0b:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 05)
0c:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02)

ss@ss-LinuxBookPro:~$ **sudo lshw -C network**
[sudo] password for ss: 
  *-network               
       description: Network controller
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:d7300000-d7303fff
  *-network
       description: Ethernet interface
       product: 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 13
       serial: 00:23:32:91:68:bd
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:d7200000-d7203fff ioport:5000(size=256) memory:db600000-db61ffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:23:12:19:53:ee
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-34-generic-pae firmware=666.2 ip=192.168.0.37 link=yes multicast=yes wireless=IEEE 802.11bg
ss@ss-LinuxBookPro:~$ 


thanks free software community;)

---

