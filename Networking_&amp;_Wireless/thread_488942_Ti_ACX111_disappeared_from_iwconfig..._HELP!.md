---
title: "Ti ACX111 disappeared from iwconfig... HELP!"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by MrGill on 2007-06-30
Having updated to 7.04 earliertoday on reboot the system had stopped recognising my Wireless card, before i had it working without Ndiswrapper, using the acx 1.2.1.34 (i think) firmware drivers, which i had to update each time i upgraded the kernal... 

but now there is no sign of wlan0 in iwconfig, or ifconfig, although it's there in lshw (as: *-network1: UNCLAIMED), and i can bring it up using lspci -vvd ...

if i run sudo lshw -short, then it is shown in the list under class network, although there is no device in the column... is there any way to associate this with the Device wlan0 ??

---

### Post by MrGill on 2007-06-30
I've copied the printouts from the other box to help:

```

mrgill@mrgill-desktop:~$ sudo lshw -short (edited)
H/W path                 Device     Class       Description
===========================================================
/0/d0000000/9                       network     ACX 111 54Mbps Wireless Interface


mrgill@mrgill-desktop:~$ sudo lspci -vvd 104c:9066
00:09.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: Abocom Systems Inc Unknown device ab90
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at cfffa000 (32-bit, non-prefetchable) [size=8K]
        Region 1: Memory at cffc0000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D3 PME-Enable- DSel=0 DScale=0 PME-

mrgill@mrgill-desktop:~$ sudo lshw (edited)
        *-network:1 UNCLAIMED
             description: Network controller
             product: ACX 111 54Mbps Wireless Interface
             vendor: Texas Instruments
             physical id: 9
             bus info: pci@00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=32
             resources: iomemory:cfffa000-cfffbfff iomemory:cffc0000-cffdffff irq:20
 
```

hope that helps

---

### Post by leo1981 on 2007-07-02
Hi,
I think I have the same problem.
Did you update the kernel at 2.6.20-16?
I think that created the problem.

dmegs

```
[  400.960000] PCI module v0.3.36 initialized, waiting for cards to probe...
[  400.984000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[  400.984000] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:5, phymem1:0x24020000, phymem2:0x24000000, mem1:0xdec64000, mem1_size:8192, mem2:0xded00000, mem2_size:131072
[  400.984000] initial debug setting is 0x000A
[  400.984000] using IRQ 5
[  400.984000] acx: need to load firmware for acx111 chipset with radio ID 16, please provide via firmware hotplug:
[  400.984000] acx: either one file only (<c>ombined firmware image file, radio-specific) or two files (radio-less base image file *plus* separate <r>adio-specific extension file)
[  400.984000] requesting firmware image 'tiacx111c16'
[  401.020000] acx: firmware image 'tiacx111c16' was not provided. Check your hotplug scripts
[  401.020000] requesting firmware image 'tiacx111'
[  401.028000] acx: firmware image 'tiacx111' was not provided. Check your hotplug scripts
[  401.028000] acx: reset_dev() FAILED
```

The driver  doesn't find the firmware.
The firmware is in:
 /lib/firmware/2.6.20-16-generic/acx/default/
I tried to copy in  /lib/firmware/ too.

Any solution?

---

### Post by MrGill on 2007-09-06
I reinstalled Ubuntu, fixed for me :lolflag:

---

### Post by ebs16 on 2007-09-10
I've run into the same problem.  Has anyone been able to fix this without a reinstall?

Thanks!

---

