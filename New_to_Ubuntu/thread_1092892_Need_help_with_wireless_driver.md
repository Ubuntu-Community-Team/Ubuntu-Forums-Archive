---
title: "Need help with wireless driver"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by cornman on 2009-03-10
Hey guys,
Here is my situation (bear with me here)
I have a dell xsp 13 with xp and ubuntu 8.04 x64
i have wireless working on ubuntu 

Here is my dilemma:
i want to install ubuntu (same version to my dell xps 13) to a flash drive, but i dont remember how i get my wireless working. All i remember is it took along time to get it working.

Here is what i need help in:
 let's say i install ubuntu to the flash drive; is there any way i could copy the wireless driver folder in my hard drive to the flash drive and skip the finding driver process?

Or, is there any way to mirror the ubuntu portion in my hard drive to the flash drive? 

my / directory is 8gb and my /home directory is 70 gb. 


Flash drive will be 16gb

i know it's kinda confusing, but thank you for reading, and im looking forward for your reply

---

### Post by adult swim on 2009-03-10
if you go to a terminal and enter in ```
lspci -k | grep Network
``` what does it return?  if it doesnt return anything, run ```
lspci -k
``` and paste all of that here.

---

### Post by cornman on 2009-03-11
the lspci -k  does not work
i got lspci: invalid option --k

but lspci i got this long list
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

```

i hope this is wat u are looking for.

but is there any way i could just copy the "/" folder from my hd and put it in my flashdrive? since it's for teh same laptop with the same config
only different is the "/home" folder size

---

### Post by adult swim on 2009-03-12
you are most likely using either b43 or ndiswrapper for your driver.  if you are using b43 you can just copy over one folder to the flash drive and get it to work. if you are using ndiswrapper there will be a few extra steps.  does b43 or ndiswrapper ring a bell?  if you cant remember post the output of ```
sudo lshw -C network
```

---

### Post by cornman on 2009-03-12
i think i use ndishwrapper (windows wireless driver?)
here is the code you ask for
```

*-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:35:86:18
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:3a:1d:4a:6a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.9 multicast=yes wireless=IEEE 802.11g


```

---

