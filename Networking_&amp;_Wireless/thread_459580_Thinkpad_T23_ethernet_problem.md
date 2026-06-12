---
title: "Thinkpad T23 ethernet problem"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by sparkroms on 2007-05-30
I was trying to updated my Xubuntu 7.04 by adding medibuntu and then downloading w32 codecs so that everything would work but in the middle of the download the speed decreases and I think that just means that it stopped downloading. I then need to reboot to be able to use the internet again. I tried going on the internet with firefox but it seems like after a certain amount of time or a certain amount of data transferred it just stops working. I tried doing

sudo modprobe e100 

but nothing shows up. Why does it only work for a little while? this is really frustrating. I searched through the forum for similar problem but everyone has trouble just connecting. Is it something to do with conflicts with e100 and the old one or something? maybe thats why the probe shows nothing? Thanks for your help.

---

### Post by sparkroms on 2007-05-31
Any output I should post here like people asked for in other threads? Should I try an older release or another version of linux?

Also whenever the internet stops working, the entire computer starts lagging at a predictable pace. If I move the mouse around, every 6 seconds it stops for a fraction of a second or so. :(

---

### Post by sparkroms on 2007-05-31
bump

---

### Post by sparkroms on 2007-05-31
sudo ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:D0:59:BE:B1:EB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0:avah Link encap:Ethernet  HWaddr 00:D0:59:BE:B1:EB  
          inet addr:169.254.11.24  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.1 KiB)  TX bytes:1200 (1.1 KiB)


sudo lspci


00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420
02:00.1 CardBus bridge: Texas Instruments PCI1420
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)


sudo lspci -v


00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: [40] Vendor Specific Information
        Capabilities: [a0] AGP version 2.0

00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: e0000000-ebffffff

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=08, sec-latency=64
        I/O behind bridge: 00002000-00006fff
        Memory behind bridge: c0200000-cfffffff
        Prefetchable memory behind bridge: f0000000-f7ffffff

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1860 [size=16]
        Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: medium devsel, IRQ 11
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
        Subsystem: IBM ThinkPad T23 (2647-4MG) or A30/A30p (2652/2653)
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]

01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05) (prog-if 00 [VGA])
        Subsystem: IBM ThinkPad T23 (2647-4MG)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at c0100000 (32-bit, non-prefetchable) [size=512K]
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Memory at e0000000 (32-bit, prefetchable) [size=32M]
        [virtual] Expansion ROM at e2000000 [disabled] [size=64K]
        Capabilities: [dc] Power Management version 2
        Capabilities: [80] AGP version 2.0

02:00.0 CardBus bridge: Texas Instruments PCI1420
        Subsystem: IBM ThinkPad T23 (2647-4MG)
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: f0000000-f3fff000 (prefetchable)
        Memory window 1: c4000000-c7fff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

02:00.1 CardBus bridge: Texas Instruments PCI1420
        Subsystem: IBM ThinkPad T23 (2647-4MG)
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 51000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=07, sec-latency=176
        Memory window 0: f4000000-f7fff000 (prefetchable)
        Memory window 1: c8000000-cbfff000
        I/O window 0: 00002800-000028ff
        I/O window 1: 00002c00-00002cff
        16-bit legacy interface ports at 0001

02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
        Subsystem: IBM Unknown device 018c
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at c0201000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 6440 [size=8]
        I/O ports at 6000 [size=256]
        Capabilities: [f8] Power Management version 2

02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at c0200000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 6400 [size=64]
        Capabilities: [dc] Power Management version 2



Theres some output that I saw someone ask for in another thread, but I am Downloading edgy now anyway since it seems to solve the ton of other problems my computer would have with Feisty Fawn.

---

### Post by sparkroms on 2007-05-31
I guess I give up then.

---

### Post by sparkroms on 2007-06-01
Well I can't give up now that Edgy does not work either. I wish someone would at least offer a little help?

---

### Post by sparkroms on 2007-06-01
Ethernet works fine in Windows Xp. I am going to try updating the Bios now and then reinstalling Edgy.

---

### Post by sparkroms on 2007-06-01
I am still having the same problem, but I learned something new.

If I do ifdown and ifup the internet starts to work again for a couple more seconds. It seems like when I send a certain amount of data that the internet stops responding.

---

### Post by terminal on 2008-01-18
I know this is old thread  but i have a solution for this .I got same problem in 7.04 , what i did is unloaded e100 and loaded eepro100 module

sudo ifconfig eth0 down
sudo rmmod e100
modprobe eepro100
sudo ifconfig eth0 up

also remove eepro100 from /etc/modprobe.d/blacklist and put e100 instead .

---

