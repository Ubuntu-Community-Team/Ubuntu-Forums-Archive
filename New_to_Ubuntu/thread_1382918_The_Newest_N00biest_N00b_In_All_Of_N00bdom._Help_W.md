---
title: "The Newest N00biest N00b In All Of N00bdom. Help With Drivers!"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by Rosc0PColtrane on 2010-01-16
Hi all!!

Just installed Ubuntu on my Compaq Presario V2000. I've had it for about 6 years and never reinstalled windows. It's been used hard and was slower than a tortoise in toffee.

Anyhoo, Ubuntu installation was easy as pie. I'm slowly getting to grips with it, but I guess I'm still in a windows mindset.

A couple teething issues I could do with some help with:

Installing the laptop drivers. While Ubuntu has provided most I need, I don't have wireless internet, and if I shut the laptop into standby, when I reopen it, it wont fire up. I have to shut it down and restart it. Not that it takes long. I found similar threads telling me to sudo apt-get bf43 install (along those lines eh??), I even found the file, downloaded it and unpacked it. The computer doesn't know the file is there. Obviously clicking or double clicking the HP exe drivers does sweet FA too. Though I notice that Ubuntu can recognise these drivers??

So, if someone can help me with the how to install driver issue, I think that will solve the wireless issue too.

Please don't assume any prior knowledge, I'm here to learn.

Thanks in advance and oh, this place looks great!!

---

### Post by WaCope on 2010-01-16
I'm assuming you have a broadcom wireless chip.  Go to System>Admin>Hardware drivers and see if there is a restricted driver available.  AFter you activate it you will need to reboot. This always works for my laptop w/a broadcom chip.

---

### Post by nothingspecial on 2010-01-16
Ignore my post count and do not assume I know anything about this - because I don`t......

......but I believe the correct command is 


```
sudo apt-get install b43-fwcutter
```

You access your terminal (where to type this) through your menus -----

----applications > accessories > terminal

---

### Post by Dude-PWB- on 2010-01-16
You need to go into a terminal and type lspci -vv and post the output of the sections regarding your networking controllers, generally it is near the bottom of the output list. Then we can make sure what networking device you have and make sure you use the appropriate drivers for it.

---

### Post by Rosc0PColtrane on 2010-01-16
> **WaCope said:**
> I'm assuming you have a broadcom wireless chip.  Go to System>Admin>Hardware drivers and see if there is a restricted driver available.  AFter you activate it you will need to reboot. This always works for my laptop w/a broadcom chip.


I assumed as much too. The Hardware Drivers window says: No proprietary drivers are in use on this computer...

---

### Post by Rosc0PColtrane on 2010-01-16
> **Dude-PWB- said:**
> You need to go into a terminal and type lspci -vv and post the output of the sections regarding your networking controllers, generally it is near the bottom of the output list. Then we can make sure what networking device you have and make sure you use the appropriate drivers for it.


Apologies for posting the whole response:

nathan@Rosc0PColtrane:~$ lspci -vv
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 64
    Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: c0100000-c01fffff
    Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel modules: shpchp

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at c0000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at c0001000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at c0002000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Region 0: I/O ports at 8400 [size=16]
    Region 1: Memory at c0003000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at 8410 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=05, subordinate=09, sec-latency=64
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: c0200000-c02fffff
    Prefetchable memory behind bridge: 20000000-23ffffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min), Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at c0003400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp

00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min), Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at c0003800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ATI IXP MC97 controller
    Kernel modules: snd-atiixp-modem

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 66 (2000ns min), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at c8000000 (32-bit, prefetchable) [size=128M]
    Region 1: I/O ports at 9000 [size=256]
    Region 2: Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon, radeonfb

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (8000ns min, 16000ns max)
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at a000 [size=256]
    Region 1: Memory at c0208000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: epl, 8139too, 8139cp

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 1355
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at c0204000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 168, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at c020a000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
    Memory window 0: 20000000-23fff000 (prefetchable)
    Memory window 1: 24000000-27fff000
    I/O window 0: 0000a400-0000a4ff
    I/O window 1: 0000a800-0000a8ff
    BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (750ns min, 1000ns max), Cache Line Size: 32 bytes
    Interrupt: pin C routed to IRQ 22
    Region 0: Memory at c0208800 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (1750ns min, 1000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at c0206000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
    Subsystem: Hewlett-Packard Company Device 3091
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (1750ns min, 1000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at c0209400 (32-bit, non-prefetchable) [size=256]
    Region 1: Memory at c0209000 (32-bit, non-prefetchable) [size=256]
    Region 2: Memory at c0208400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

---

### Post by Dude-PWB- on 2010-01-16
This is indeed your wireless device. So this should help you in your search to get the proper drivers installed and working.

```
05:02.0 **Network controller: Broadcom Corporation BCM4318** [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 1355
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at c0204000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
```

---

### Post by Rosc0PColtrane on 2010-01-16
Excellent, thanks!

So following this guide: [http://ubuntuforums.org/showthread.php?t=285809](http://ubuntuforums.org/showthread.php?t=285809)  should get me the correct result?

I have downloaded drivers already, but am struggling with how to install them. I may already have the correct drivers unpacked!

Thanks again for your help!

---

### Post by Dude-PWB- on 2010-01-16
If you can temporarily connect to a wired internet connection then try what nothingspecial has posted in post #3 about installing b43-fwcutter.

I always considered using ndsiwrapper and windows drivers as a 'last resort' when it comes to linux.

---

### Post by Rosc0PColtrane on 2010-01-16
> **Dude-PWB- said:**
> If you can temporarily connect to a wired internet connection then try what nothingspecial has posted in post #3 about installing b43-fwcutter.

I always considered using ndsiwrapper and windows drivers as a 'last resort' when it comes to linux.

Is ndsiwrapper a bodge to use windows drivers then??

I'd tride the sudo command earlier, just tried it again:

nathan@Rosc0PColtrane:~$ sudo apt-get install b43-fwcutter
[sudo] password for nathan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter
nathan@Rosc0PColtrane:~$

---

### Post by nothingspecial on 2010-01-16
> **Rosc0PColtrane said:**
> Is ndsiwrapper a bodge to use windows drivers then??

I'd tride the sudo command earlier, just tried it again:

nathan@Rosc0PColtrane:~$ sudo apt-get install b43-fwcutter
[sudo] password for nathan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter
nathan@Rosc0PColtrane:~$

That is probably because you don`t have an internet connection, if you can get a wired one, try it again.

The command is to install a driver over the internet so, if you don`t have a connection, it will not work.

---

### Post by Rosc0PColtrane on 2010-01-16
> **nothingspecial said:**
> That is probably because you don`t have an internet connection, if you can get a wired one, try it again.

The command is to install a driver over the internet so, if you don`t have a connection, it will not work.


That's with the internet connection wired in. I ran it then posted the response here via my laptop!!!

Can I ping test through the terminal, to check it's connected ok?

---

### Post by nothingspecial on 2010-01-16
Have you updated since you installed

```
sudo apt-get update && sudo apt-get install b43-fwcutter
```

I`m not being funny but it`s in the repos

```
:~$ apt-cache search b43-fwcutter
b43-fwcutter - Utility for extracting Broadcom 43xx firmware
```

EDIT ****** And Congratulations, You are the recipient of my 2500th support post ....... Some people have had better help.....anyway we`ll keep going.....like I said, I know nothing of broadcom wireless drivers anyway.....



..... but alot of people do, don`t worry it`ll work in the end.

---

### Post by mkoyle on 2010-01-16
If updating like nothingspecial said doesn't help, the next possibility is that online repositories didn't get set up... maybe you installed with no internet connection available?  I have seen offline installs result in the online repositories being disabled.  

It's all explained at [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

But, so that you don't have to poke through all of that you can use Synaptic: System > Administration > Synaptic >> Settings >> Repositories.  If you want to see that file that that edits, it can be edited manually with:

```
sudo nano /etc/apt/sources.list
```

---

### Post by Rosc0PColtrane on 2010-01-17
> **nothingspecial said:**
> Have you updated since you installed

```
sudo apt-get update && sudo apt-get install b43-fwcutter
```I`m not being funny but it`s in the repos

```
:~$ apt-cache search b43-fwcutter
b43-fwcutter - Utility for extracting Broadcom 43xx firmware
```EDIT ****** And Congratulations, You are the recipient of my 2500th support post ....... Some people have had better help.....anyway we`ll keep going.....like I said, I know nothing of broadcom wireless drivers anyway.....



..... but alot of people do, don`t worry it`ll work in the end.

I feel honoured to be the recipient of such a momentous milestone!!! Congratulations!!

The update worked a charm, so did the b43 fwcutter request. Terminal shows it as extracted. Thanks. 

Now to see if I can get the wireless to work. Must need to do something more, the wireless button isn't working....

Thanks for all your input!

---

### Post by Rosc0PColtrane on 2010-01-17
Am I missing something here? I've extracted the files, the System > Hardware Drivers show it as installed but the wireless button doesn't work. In windows, I could switch it on and off in the desktop as well as the physical button. Can I do this with ubuntu?

I'd also going to need to get my webcam working, will ubuntu drivers do the trick or will I need to source a work around?

I also used to plug my laptop into my tv to watch films, does ubuntu offer the same control, or will I need the nvidia GPU contoller?


Thanks for your patience!!

---

### Post by bkratz on 2010-01-17
> **Rosc0PColtrane said:**
> Am I missing something here? I've extracted the files, the System > Hardware Drivers show it as installed but the wireless button doesn't work. In windows, I could switch it on and off in the desktop as well as the physical button. Can I do this with ubuntu?

I'd also going to need to get my webcam working, will ubuntu drivers do the trick or will I need to source a work around?

I also used to plug my laptop into my tv to watch films, does ubuntu offer the same control, or will I need the nvidia GPU contoller?


Thanks for your patience!!



Two things:

1) When you mentioned ndiswrapper earlier in the post did you actually install it too? 
2) After you did the correct update to the b43 drivers did you reboot? It is necessary and may require a power down not just a restart.

Here is a thread regarding what you are trying to do. See post #9 specifically, this person has the same card you do.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Rosc0PColtrane on 2010-01-17
> **bkratz said:**
> Two things:

1) When you mentioned ndiswrapper earlier in the post did you actually install it too? 
2) After you did the correct update to the b43 drivers did you reboot? It is necessary and may require a power down not just a restart.

Here is a thread regarding what you are trying to do. See post #9 specifically, this person has the same card you do.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)


1)No, another poster viewed it as a 'last resort'. As I bow to ther greater knowledge, I followed that accepted wisdom and have not. Though I'm guessing I may need it to accomplish what I want from my laptop...
2)Yes, will try again, none-the-less!!

Thanks, for the link. Will fire up the lappy and work through it. That's very helpful!!

---

### Post by bkratz on 2010-01-17
> **Rosc0PColtrane said:**
> 1)No, another poster viewed it as a 'last resort'. As I bow to ther greater knowledge, I followed that accepted wisdom and have not. Though I'm guessing I may need it to accomplish what I want from my laptop...
2)Yes, will try again, none-the-less!!

Thanks, for the link. Will fire up the lappy and work through it. That's very helpful!!

1) That is good ( otherwise we would have to remove it ) to use the native driver.

---

### Post by Rosc0PColtrane on 2010-01-17
Case closed. Rebooted again and the wireless light is working. All connected. Thank you all so much for your help. I appreciate it.

This forum looks great, hope I'm around for a while!!!

---

### Post by nothingspecial on 2010-01-17
Told you so :D

---

### Post by Rosc0PColtrane on 2010-01-17
Yes, yes you did!!!

Now onto my next task: Dual screening!!!

---

### Post by bkratz on 2010-01-17
Congratulations!  It was easy wasn't it?

---

### Post by Rosc0PColtrane on 2010-01-18
> **bkratz said:**
> Congratulations!  It was easy wasn't it?

Only because I had great help!!!

Thanks again!!!


Dual screening seems to be a little tougher.

---

