---
title: "1st timer NEED HELP PLEASE"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by omid429 on 2009-12-14
I am having problems getting drivers to work and using plugins on fw170j. microphone works at an extremely low level even with full amplification. flash not working with firefox or chrome. cannot access network storage. I also want to know if linux is recognizing the swap drive? the linux documentation is of little help. it only tells me to install the plugin and thats it. I get that from windows. anyway, I am a COMPLETE noob to linux. I would like any help on these specific issues as well as any links to any type of beginner's guide to karmic koala terminal. I need to learn the code more than anything. Thanks all.
 oh and if you wanna know more specifics, keep reading. So here's my story. I installed karmic koala using the windows launcher from win 7. oh yeah, hard drive is partitioned as follows: 

1. recovery ~9gb
2. win7 ~175gb, ntfs
3. swap ~10gb, unix
4. linux ~33gb, ntfs
5. data ~75gb, ntfs

after install, i was having issue with the swap drive. so I created an ubuntu 9.1 install cd and used the partitioner on the cd to create a swap drive (3) and install a new copy of ubuntu over the one I just installed...(I am sure that I have done some really dumb noob things, but bear with me, please). anyway, now the dual boot screen turned into a multi stage dual boot screen starting with the cd_install boot screen folowed by the boot screen caused by the win_install. also, the linux drive (4) and swap drive (3) were formatted in a file format that win 7 didn't recognize. in any case, I had messed up the MBR and was just getting annoyed now. So I finally logged back into windows, formatted drives 2,4, and 5 and reinstalled win7 from scratch on 2. than i installed linux back on 4 using the windows installer. so now here I am, dual booting win 7 and karmic koala and trying to learn my way around linux.

---

### Post by LowSky on 2009-12-14
Welcome to the Ubuntu Forums, hope we can help!

Lets try to figure out what you did
Can you answer these to the best of your knowlege...

1. you dont need 10GB for Swap, at most you need is 2GB. the more RAM you have the less this is important. You'll only need it for really crazy things like running 10000 apps at one time.
2. Ubuntu now uses a filesystem called EXT4 by default, Windows cannot read it unfortunatly, thats just the way it is, and actually a good thing too, If it cant read it then viruses cant infect it... Also NTFS should never be used for a Linux file system, its not designed to work correctly.
3. A hard drive can only have 4 logical partitions, you can however have many more if you create an extended partition. I'm not sure how you installed it t begin with so that brings me to my next question...
4. Where is the Windows 7 boot loader partiton, My install has one, so I'm wondering where yours is.
5. fw170j is a  Sony Viao correct?
6. Did you install Ubuntu from inside Windows or did you use the LiveCD and install by booting the machine form the DVD-ROM?


here are some Great sites to look at for some knowlege building
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[https://help.ubuntu.com/9.10/index.html](https://help.ubuntu.com/9.10/index.html)
[http://www.ubuntu.com/support/CommunitySupport](http://www.ubuntu.com/support/CommunitySupport)

---

### Post by omid429 on 2009-12-14
thanks lowsky for your interest. I appreciate it.

1. while reading, I read that the swap should be 2x the RAM and I have 4gb, so I set if ro ~10gb.
2. 1st install was through windows on an ntfs file system (4) created in windows. while researching, I learned that the windows installer creates a file with size 30gb that linux rewrites as its own filesystem. this allows the partition to be recognized as ntfs by windows, while still allowing linux to run. 2nd install was with ubuntu disk (mostly to create a swap drive because a few forums told me I needed one...not sure exactly for what, I thought it was for running programs...sort of like RAM). then logged back into windows and manually deleted linux file which screwed up mbr and called for fresh install of everything. so then was 3rd install which was after a fresh win7 install and linux was installed again using windows installer.
3. recovery and win7 are primary, the other three are logical
4. on the windows partition.
5. yeah it is a sony vaio. I have searched specifically for problems with flash and the mic using my model as a search string and there are others with this problem and no solution I can understand. 
6. 3rd and last install which is where I currently am was through windows installer. this is why i want to know if there is a way to check to see if it recognizes the partition i used as a swap drive as the swap drive. if not, how do i set it to use it as the swap drive. or should i just format it back to another file system all together?

---

### Post by omid429 on 2009-12-14
UPDATE: I installed all flash plugins available at the software center and now I can play about half of everything at youtube.

---

### Post by LowSky on 2009-12-14
> **omid429 said:**
> thanks lowsky for your interest. I appreciate it.

1. while reading, I read that the swap should be 2x the RAM and I have 4gb, so I set if ro ~10gb.
That logic made sense years ago, but now with most PC having over 2GB of RAM is become kinda overkill to use so much SWAP when the facts are you probably wont ever use it.

> **omid429 said:**
> 
2. 1st install was through windows on an ntfs file system (4) created in windows. while researching, I learned that the windows installer creates a file with size 30gb that linux rewrites as its own filesystem. this allows the partition to be recognized as ntfs by windows, while still allowing linux to run. 2nd install was with ubuntu disk (mostly to create a swap drive because a few forums told me I needed one...not sure exactly for what, I thought it was for running programs...sort of like RAM). then logged back into windows and manually deleted linux file which screwed up mbr and called for fresh install of everything. so then was 3rd install which was after a fresh win7 install and linux was installed again using windows installer.
Well first you didn't need to reinstall anything,  A windows install CD could have fixed you MBR using the recovery option. Its a hidden back door menu, so don't feel bad. 


> **omid429 said:**
> 3. recovery and win7 are primary, the other three are logical ah OK


> **omid429 said:**
> 4. on the windows partition. ok odd to me but if it works


> **omid429 said:**
> 5. yeah it is a sony vaio. I have searched specifically for problems with flash and the mic using my model as a search string and there are others with this problem and no solution I can understand. 
 most likely need to do some command line stuff first thing you need to do is open up a terminal
Applications>Accessories>Terminal

type this command

```
lspci -vv
```
Its going to spew a whole lot of words back at you, all this stuff is, is the chipsets by there make and model, knowing them exactly will really help us. just copy and paste the info here so we can have a look. Use  CODE tags, available from the advanced post option so that the data doesn't end up having any of these little guys :D 8) it happens from time to time

> **omid429 said:**
> 6. 3rd and last install which is where I currently am was through windows installer. this is why i want to know if there is a way to check to see if it recognizes the partition i used as a swap drive as the swap drive. if not, how do i set it to use it as the swap drive. or should i just format it back to another file system all together? 
dont re-format unless you really want the space back. Better to use this install as testing grounds, More than likely you will break something and need to find out how to fix or reinstall. Learning a new Os isn't easy so take some time,  use this install and have fun learning. Hopefully we can fix your sound issue.

Lastly hese a sample of the lspci --v code will give you, note this is mine and will greatly differ from yours.

```
john@john-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:05.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port B)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
05:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)
05:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)

```

---

### Post by Geoff918 on 2009-12-14
Fastest way to media is the following:

Install package called:

ubuntu-restricted-extras

With the recording level check the following:

Alt-F2 (check the box that says "Run In Terminal")

Input: alsamixer

Make sure your line-in is all the way at 100 or whatever is comfortable.

Press ESC to exit

---

### Post by omid429 on 2009-12-15
sorry for the late response...win7 decided updates were necessary, then froze, and proceeded to make my life a nightmare. in any case, I said screw it and started over. current setup is as follows (not that much changed, but this way, everything makes sense):

partition 1: recovery (vistaHPsp1)
partition 2: win7 ntfs
3: swap ext4
4: linux ext4
5: data ntfs

all sizes are the same. as a result of installing linux its way and without the windows installer, I fixed my flash problem. videos work perfect now, yay. microphone is still having recording issues, and network drives are still unaccessible (i bet this is an easy fix if I knew the proper syntax and menu choices for Places>Connect to server...?). since I installed with the cd, I am sure the swap drive is as it should be, though apparently larger than it should be ;). i typed in that code you told me to about listing my hardware and I have it pasted below. I am assuming the code 'lspci' stood for "list pci" but what does the '-vv' stand for? 

@geoff
thanx for the idea. you were right the mixer had both 'Mic' and 'Atapi Mi' both were set to zero. I turned them both all the way up but alas, no luck. 



```
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Sony Corporation Device 9035
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 19
    Region 0: Memory at d5604c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at d5600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: d4100000-d54fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d2d00000-d40fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d1900000-d2cfffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=07, subordinate=08, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d0500000-d18fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 4: I/O ports at 60a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at 6080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at 6060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 16
    Region 4: I/O ports at 6040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Sony Corporation Device 9035
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at d5604800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
    Memory behind bridge: d5500000-d55fffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 28
    Region 0: I/O ports at 6130 [size=8]
    Region 1: I/O ports at 6120 [size=4]
    Region 2: I/O ports at 6110 [size=8]
    Region 3: I/O ports at 6100 [size=4]
    Region 4: I/O ports at 6020 [size=32]
    Region 5: Memory at d5604000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 5
    Region 0: Memory at d5605000 (64-bit, non-prefetchable) [disabled] [size=256]
    Region 4: I/O ports at 6000 [size=32]
    Kernel modules: i2c-i801

05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
    Subsystem: Intel Corporation Device 1301
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 31
    Region 0: Memory at d1900000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 30
    Region 0: Memory at d0520000 (64-bit, non-prefetchable) [size=16K]
    Region 2: I/O ports at 2000 [size=256]
    Expansion ROM at d0500000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

09:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
    Subsystem: Sony Corporation Device 9035
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at d5500000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

09:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    Subsystem: Sony Corporation Device 9035
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at d5500900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

09:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Sony Corporation Device 9035
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 4
    Region 0: Memory at d5500800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

otto@Sony2008:~$ cls
No command 'cls' found, but there are 21 similar ones
cls: command not found
otto@Sony2008:~$ clear

otto@Sony2008:~$ lspci-vv
lspci-vv: command not found
otto@Sony2008:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Sony Corporation Device 9035
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 29
    Region 0: Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at 6140 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at d0400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at 60e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 21
    Region 4: I/O ports at 60c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Sony Corporation Device 9035
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 19
    Region 0: Memory at d5604c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at d5600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: d4100000-d54fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d2d00000-d40fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d1900000-d2cfffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=07, subordinate=08, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d0500000-d18fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 4: I/O ports at 60a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at 6080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at 6060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 16
    Region 4: I/O ports at 6040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Sony Corporation Device 9035
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at d5604800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
    Memory behind bridge: d5500000-d55fffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 28
    Region 0: I/O ports at 6130 [size=8]
    Region 1: I/O ports at 6120 [size=4]
    Region 2: I/O ports at 6110 [size=8]
    Region 3: I/O ports at 6100 [size=4]
    Region 4: I/O ports at 6020 [size=32]
    Region 5: Memory at d5604000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 5
    Region 0: Memory at d5605000 (64-bit, non-prefetchable) [disabled] [size=256]
    Region 4: I/O ports at 6000 [size=32]
    Kernel modules: i2c-i801

05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
    Subsystem: Intel Corporation Device 1301
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 31
    Region 0: Memory at d1900000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
    Subsystem: Sony Corporation Device 9035
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 30
    Region 0: Memory at d0520000 (64-bit, non-prefetchable) [size=16K]
    Region 2: I/O ports at 2000 [size=256]
    Expansion ROM at d0500000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

09:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
    Subsystem: Sony Corporation Device 9035
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at d5500000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

09:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    Subsystem: Sony Corporation Device 9035
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at d5500900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

09:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Sony Corporation Device 9035
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 4
    Region 0: Memory at d5500800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>



```

---

### Post by LowSky on 2009-12-15
to fix sound open a terminal
type this command
```
gksu getdit /etc/modprobe.d/alsa-base.conf
```
 look for this
```
options snd-hda-intel 
```
make sure this appears next to it, it not change it to match
```
model=auto
```
 should now look like this
```
options snd-hda-intel model=auto
```
reboot and mic should work





found info in this bug report
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478309](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478309)

---

### Post by omid429 on 2009-12-15
Low Sky,

when I typed the code the first time, it asked for my admin password. I typed in the password and then it just returned to prompt. I retyped it and still got no results.
when I tried typing in the next line it said 'options' was not a recognized command. yeah, i know it was dumb, but I had to try it.

also, is there a website that has a list of terminal commands along with explanations. I would prefer it to be beginner commands just to get myself acquainted with the commands and syntax. thanks.

---

### Post by omid429 on 2009-12-15
[UPDATE]

I have learned that I can access my NAS drives by opening a browser window and typing:
smb://<IP>

However I still cannot mount these drives. When I try to access them using Places>Connect to Server and setting windows share, it access the drives but requests a user name and password. there is no user name and password and the access point that the NAS is connected to is not set as a DHCP server. It is set by the main router. This problem occurs in windows 7 too but for some reason is only temporary and only pops up when I access any of the partitions the first time.

---

### Post by omid429 on 2009-12-15
[UPDATE]

I have located a forum for editing my fstab file to mount my NAS drives on startup. however, I am running into problems. when I try to use the 'Places>Connect to Server' it doesn't access because it asks for a password. I am having the same issue when I edit the fstab file.

This is the link to the webpage where I have acquired the code:
[http://www.marcus-furius.com/?p=59](http://www.marcus-furius.com/?p=59)

THis is the code as it is now
```

//192.168.20.42/MEDIA /media/MEDIA/ cifs nounix,uid=otto,gid=users,file_mode=0777,dir_mode=0777,username=,password= 0 0

```

THe problem is that there is no user name or password to access these drives. How can I enter null into username and password? Or better yet, what do I do.?..HELP!

---

