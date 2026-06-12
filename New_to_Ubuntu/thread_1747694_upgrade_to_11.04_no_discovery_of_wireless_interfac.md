---
title: "upgrade to 11.04 no discovery of wireless interface"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by MurphysLaww on 2011-05-02
running a Dell Precision m6300 with the broadcom additional driver activated

This one:

This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.

Ran install, it finished, restarted, and my wireless is gone. I disabled the broadcom driver, restarted, then re-installed it, but there is still no discover of the wireless card.

At a loss now. I guess maybe I should have plugged into a wired connection when doing the install.

The wired interface is fine.

Any help would be appreciated.

---

### Post by josephmills on 2011-05-03
could you open up your terminal and type in 
```

sudo lshw -c network

```
and paste here thanks also it takes a bit to load

---

### Post by 3rdalbum on 2011-05-03
Reinstall the Broadcom driver. Shut the computer down COMPLETELY (i.e. a shutdown, not a restart) and see if it works now.

---

### Post by MurphysLaww on 2011-05-03
Here is the output.

I searched a bit deeper in the installation/upgrade section and it seems like this a dell wireless card issue. looks like Natty doesn't like the firmware for this card and either discards it, or can no longer link to it.

Ohh, well. New ubuntu is pretty much the same as ubuntu several years ago. Always something, or some part it doesn't support. I had high hopes, enough to drop from a dual boot to just ubuntu. Looking like that may have been a mistake, or I should have just left well enough alone with the last release, which worked with the STA driver.




 *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f1ffc000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5756ME Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5756m-v3.09 ip=192.168.0.195 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:45 memory:f1bf0000-f1bfffff

---

### Post by josephmills on 2011-05-03
```

lspci -nn

```
thanks

---

### Post by MurphysLaww on 2011-05-03
Worked through most of this as well, but no-go

[http://ubuntuforums.org/showthread.php?t=1742147](http://ubuntuforums.org/showthread.php?t=1742147)

shawnp@shawnp-Precision-M6300:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller [8086:2811] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G84 [Quadro FX 1600M] [10de:040d] (rev a1)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5756ME Gigabit Ethernet PCI Express [14e4:1674]
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

---

### Post by MurphysLaww on 2011-05-03
For whatever reason, this worked this time...

sudo modprobe --ignore-install b43

perhaps the issue was rebooting after some of the other processes that I went through earlier instead of a shutdown.

Regardless thanks for the help !

***update***

This appears to be some sort of issue with the function key calls, as you can function key shut down the wireless and then it's gone. You can't re-key it and turn it back on. You then have to shut-down the machine, bring it back up and run > sudo modprobe --ignore-install b43 again.

And, I have to run that command everytime I start-up now. Something is definitely broke.

---

