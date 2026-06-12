---
title: "Unable to get wireless on Ubuntu 7.10"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by ACmilan on 2008-01-15
Hello,
 I have an acer c310 tablet and started using ubuntu about a year and a half ago. It worked flawlessly until 7.10 when i started having trouble with the wireless. In network manager there is no option for wireless networks at all, only configure manually and wired networks. I have looked at restricted drivers to check my wireless card but it says it is recognized. Sometimes, right after i upgraded to 7.10, there were times when i could restart my computer and it would turn the wireless back on, but recently it has been off for 4 days and i need it for school. Any help would be greatly appreciated.
Thanks

edit: I have tried sudo ifdown lo and sudo ifup lo again, i have also done sudo ifconfig lo...none of these have helped at all.

---

### Post by csat on 2008-01-15
First of all I suggest you to inform which wireless board are you using so that we can address or not to a proper tutorail/thread.  You can find it going to a console terminal and typing sudo lspci -v

---

### Post by ACmilan on 2008-01-17
im a stupid noob so i dont know which part says that in lspci -v but the acer website says its an intel pro/wireless 2200bg

---

### Post by jank on 2008-01-17
if you don't know just post everything we'll figure out.

---

### Post by Hightide on 2008-01-17
can you post the output as of

lshw -C network    

go to  Applications/accessories/terminal and paste

:)

---

### Post by ACmilan on 2008-01-17
Sorry for the delay and how big it is,I just included everything there was from results of lspci -v and lshw -C network below, they are seperated. thanks

[SIZE="3"]lspci -v[/SIZE]
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, fast devsel, latency 0

        Capabilities: [e0] Vendor Specific Information



00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])

        Flags: bus master, fast devsel, latency 0

        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0

        Memory behind bridge: 90000000-afffffff

        Prefetchable memory behind bridge: c0000000-cfffffff

        Capabilities: [88] Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Capabilities: [80] Power Management version 2

        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

        Capabilities: [a0] Express Root Port (Slot+) IRQ 0



00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) (prog-if 00 [Normal decode])

        Flags: bus master, fast devsel, latency 0

        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0

        Capabilities: [40] Express Root Port (Slot+) IRQ 0

        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

        Capabilities: [90] Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Capabilities: [a0] Power Management version 2



00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04) (prog-if 00 [Normal decode])

        Flags: bus master, fast devsel, latency 0

        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0

        I/O behind bridge: 00003000-00003fff

        Memory behind bridge: b0000000-b3ffffff

        Prefetchable memory behind bridge: 00000000d0000000-00000000d3ffffff

        Capabilities: [40] Express Root Port (Slot+) IRQ 0

        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

        Capabilities: [90] Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Capabilities: [a0] Power Management version 2



00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, medium devsel, latency 0, IRQ 20

        I/O ports at 1800 [size=32]



00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, medium devsel, latency 0, IRQ 17

        I/O ports at 1820 [size=32]



00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, medium devsel, latency 0, IRQ 21

        I/O ports at 1840 [size=32]



00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, medium devsel, latency 0, IRQ 22

        I/O ports at 1860 [size=32]



00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, medium devsel, latency 0, IRQ 20

        Memory at 80000000 (32-bit, non-prefetchable) [size=1K]

        Capabilities: [50] Power Management version 2

        Capabilities: [58] Debug port



00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])

        Flags: bus master, fast devsel, latency 0

        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=216

        I/O behind bridge: 00004000-00004fff

        Memory behind bridge: b4000000-b40fffff

        Prefetchable memory behind bridge: 0000000030000000-0000000035ffffff

        Capabilities: [50] Subsystem: Acer Incorporated [ALI] Unknown device 006a



00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

        Subsystem: Acer Incorporated [ALI] Realtek ALC 655 codec (in Acer TravelMate 2410 serie laptop)

        Flags: bus master, medium devsel, latency 0, IRQ 19

        I/O ports at 1c00 [size=256]

        I/O ports at 1880 [size=64]

        Memory at 80000800 (32-bit, non-prefetchable) [size=512]

        Memory at 80000400 (32-bit, non-prefetchable) [size=256]

        Capabilities: [50] Power Management version 2



00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04) (prog-if 00 [Generic])

        Subsystem: Acer Incorporated [ALI] Conexant AC'97 CoDec (in Acer TravelMate 2410 serie laptop)

        Flags: bus master, medium devsel, latency 0, IRQ 19

        I/O ports at 2400 [size=256]

        I/O ports at 2000 [size=128]

        Capabilities: [50] Power Management version 2



00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, medium devsel, latency 0



00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04) (prog-if 8a [Master SecP PriP])

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, medium devsel, latency 0, IRQ 16

        I/O ports at 01f0 [size=8]

        I/O ports at 03f4 [size=1]

        I/O ports at 0170 [size=8]

        I/O ports at 0374 [size=1]

        I/O ports at 18c0 [size=16]



00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: medium devsel, IRQ 11

        I/O ports at 20a0 [size=32]



01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1) (prog-if 00 [VGA])

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, fast devsel, latency 0, IRQ 16

        Memory at a0000000 (32-bit, non-prefetchable) [size=16M]

        Memory at c0000000 (64-bit, prefetchable) [size=128M]

        Memory at 90000000 (64-bit, non-prefetchable) [size=16M]

        [virtual] Expansion ROM at c8000000 [disabled] [size=128K]

        Capabilities: [60] Power Management version 2

        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

        Capabilities: [78] Express Endpoint IRQ 0



06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 23

        I/O ports at 4000 [size=256]

        Memory at b4006000 (32-bit, non-prefetchable) [size=256]

        [virtual] Expansion ROM at 34000000 [disabled] [size=128K]

        Capabilities: [dc] Power Management version 2



06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, medium devsel, latency 168, IRQ 18

        Memory at b4007000 (32-bit, non-prefetchable) [size=4K]

        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176

        Memory window 0: 30000000-33fff000 (prefetchable)

        Memory window 1: 38000000-3bfff000

        I/O window 0: 00004400-000044ff

        I/O window 1: 00004800-000048ff

        16-bit legacy interface ports at 0001



06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, medium devsel, latency 32, IRQ 18

        Memory at b4006800 (32-bit, non-prefetchable) [size=2K]

        Memory at b4000000 (32-bit, non-prefetchable) [size=16K]

        Capabilities: [44] Power Management version 2



06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, medium devsel, latency 57, IRQ 18

        Memory at b4004000 (32-bit, non-prefetchable) [size=8K]

        Capabilities: [44] Power Management version 2



06:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

        Subsystem: Acer Incorporated [ALI] Unknown device 006a

        Flags: bus master, medium devsel, latency 57, IRQ 18

        Memory at b4008400 (32-bit, non-prefetchable) [size=256]

        Memory at b4008000 (32-bit, non-prefetchable) [size=256]

        Memory at b4006400 (32-bit, non-prefetchable) [size=256]

        Capabilities: [80] Power Management version 2





[SIZE="3"]lshw -C network[/SIZE]


*-network               

       description: Ethernet interface

       product: RTL-8169 Gigabit Ethernet

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 7

       bus info: pci@0000:06:07.0

       logical name: eth0

       version: 10

       serial: 00:0a:e4:e1:61:d5

       size: 100MB/s

       capacity: 1GB/s

       width: 32 bits

       clock: 66MHz

       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s

---

### Post by kure-ji on 2008-01-18
faced the same problem too... after much hair loss, i finally stumbled upon the solution...
basically wad you need to do is to make a linux header then followed by updating your IEEE 802.11 and your firmware.

here's how it's done:

```
cat /proc/version
```
this is to find your linux kernel version

```
apt-get install linux-headers-<version number>
```
to install the headers.

Following that,

```
sudo apt-get install build-essential ieee80211-source
```
for dependencies

u'll need to download the required files,
```
wget http://internap.dl.sourceforge.net/sourceforge/ieee80211/ieee80211-1.2.18.tgz
wget http://internap.dl.sourceforge.net/sourceforge/ipw2200/ipw2200-1.2.2.tgz
wget http://bughost.org/firmware/ipw2200-fw-3.0.tgz
```

then to install all the above stuff,

```
tar xvf ieee80211-1.2.18.tgz
tar xvf ipw2200-1.2.2.tgz
tar xvf ipw2200-fw-3.0.tgz
cd ieee80211-1.2.18/
sudo make #hit enter (y), it asks to remove old files/comment definitions
sudo make install
cd ./../ipw2200-1.2.2/
sudo sh remove-old #hit enter (y) to all quesitons
sudo make
sudo make install
cd ./../ipw2200-fw-3.0/
sudo cp *.* /lib/firmware/
```

then restart...

hope this helps!

---

### Post by ACmilan on 2008-01-20
Thanks! I haven't been able to try this yet but hopefully it works.:)

---

### Post by kure-ji on 2008-01-31
so does it work? if it does, could you mark the topic as solved?
:)

---

### Post by ACmilan on 2008-02-04
Unfortunately not, I've come to the conclusion that my wireless card is just not being recognized.  I've even booted off the live cd and there is no wireless aswell. On top of this I am a total noob and do not know how to fix this by myself. If anyone has any ideas or thoughts i'd really appreciate it, it would prevent me from having to go back to XP. 
thanks in advance,

-The wireless card is recognized but not working. Also there is still no wireless option in network manager at all, only wired and dial-up.

---

### Post by Zeroa on 2008-02-04
Yeah.

---

