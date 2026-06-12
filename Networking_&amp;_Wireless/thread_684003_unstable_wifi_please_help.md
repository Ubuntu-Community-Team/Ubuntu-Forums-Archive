---
title: "unstable wifi please help"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by darkmdbeener on 2008-01-31
i have the broadcome 43xx chipset. 
ill be able to surf for a few sec then i can do anything and it still will say that i am connected. how do i fix this, i herd of madwifi in my search but i dont know what this is. 

please help
thanks,
beener

---

### Post by reckless2k2 on 2008-01-31
how did you get your wifi going or did it work out of box? also, post the results of this form the terminal:

```
lspci -v
```

we can get on track. also, are you connecting to your net or another person's like community net...how far away..yadda. just some more details please. romaing will need to be disabled as well if i'm not mistaken in the network config. 

someone tag in on the help here. thanks.

---

### Post by kevdog on 2008-01-31
madwifi is for atheros chipsets.  You have a broadcom chipset.  Rather than using the bcm43xx driver, Id recommned ndiswrapper + winxp driver due to stability.

---

### Post by darkmdbeener on 2008-01-31
well i got it work useing the restricted driver
and its an intergrated wireless card also

right now im useing th wireless it just take about 3 min of connecting and reconecting to become stable

and alil while ago i dl the packe madwifi-tools
bu i dont know what it does. so im at a los there

here is the lspci you asked for i dont know how to put it in to the code thing though sorry

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at b0000000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: fast devsel
        Memory at 34000000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 0, IRQ 17
        Memory at b0040000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=216
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: b0100000-b01fffff
        Prefetchable memory behind bridge: 0000000030000000-0000000033ffffff
        Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at b0040800 (32-bit, non-prefetchable) [size=512]
        Memory at b0040400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: medium devsel, IRQ 3
        I/O ports at 20a0 [size=32]

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at 3000 [size=256]
        Memory at b0108000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

06:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1355
        Flags: bus master, fast devsel, latency 32, IRQ 19
        Memory at b0104000 (32-bit, non-prefetchable) [size=8K]

06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at b010a000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 30000000-33fff000 (prefetchable)
        Memory window 1: 38000000-3bfff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at b0108800 (32-bit, non-prefetchable) [size=2K]
        Memory at b0100000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 57, IRQ 16
        Memory at b0106000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

06:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 57, IRQ 16
        Memory at b0109400 (32-bit, non-prefetchable) [size=256]
        Memory at b0109000 (32-bit, non-prefetchable) [size=256]
        Memory at b0108400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by darkmdbeener on 2008-01-31
where can i get the wifi driver then the last time i try to use ndiswrapper for my self it never worked, and 
how to i go about switching over to just useing that wireless driver

thought i edited but quated sorry

---

