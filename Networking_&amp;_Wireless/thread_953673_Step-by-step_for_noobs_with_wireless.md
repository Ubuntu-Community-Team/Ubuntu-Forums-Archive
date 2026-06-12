---
title: "Step-by-step for noobs with wireless?"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by Gennn89 on 2008-10-20
Hey linux nerds out there, If you think you know ubuntu could you help a poor noob set up a wireless from home here? Played with terminal, network manager and every tool i could think of and all i could get for internet was using the ethernet cable plugged in. just cant figure out the wireless stuff at all. pm, email (dj_ortana@hotmail.com) or call please (B.C. Canada if your in the okanagan 250-803-2367) help needed stat if your nice enough to take some time and actually fix the problem by calling that would be even better thanks - Noah

---

### Post by Idefix82 on 2008-10-20
Please open the terminal and give us the output from the commands
```
lshw-C network
```
and
```
lspci
```
so we know what hardware you are using.

---

### Post by Gennn89 on 2008-10-20
noah@Noah-Laptop:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

noah@Noah-Laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

---

### Post by Ayuthia on 2008-10-20
If I recall correctly, if you have a working connection in Ubuntu, get your system current and then go to System->Administration->Hardware Drivers and select the Broadcom driver (should be wl or Broadcom STA).

If I recall correctly, the driver for your card was not introduced into Hardy until 2.6.24-17 so the driver is not found on the initial install of 8.04.  However, the 8.04.1 live CD does have it available.

---

### Post by Gennn89 on 2008-10-20
I have Wl showing there and its enabled so what do i do now? are you saying i need to download a new version of ubuntu or download upgrade packages or what do i do?

---

### Post by Idefix82 on 2008-10-20
I think that is the driver Ayuthia was looking for. You should be able to see the wireless networks in reach if you left click on the network manager icon in the top right corner. That's also where you connect to a network.

Apologies, the command I gave you was misspelled. It should have been
```
lshw -C network
```
but you won't need it if you can connect to a network from the network manager.

---

### Post by Gennn89 on 2008-10-20
wireless networknot appearing when i left click
what is the network manager how do i get to it

---

### Post by Ayuthia on 2008-10-20
> **Gennn89 said:**
> wireless networknot appearing when i left click
what is the network manager how do i get to it

I think that the part where you are left-clicking is the network manager that we are talking about.  If you don't see any wireless sites, can you go back into the Terminal and post the results of:
```
lshw -C network
```It does have to be a big C instead of the lower-case one.  Linux is case sensitive.

---

