---
title: "ubuntu doesn't recognise my tuner card"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by bance on 2010-07-24
Hi guys,

I have a Avermedia avertv dvb-t super 007 tuner card. I'm hoping to get this working in my ubuntu set up

Linux master-backend
 2.6.32-23-generic #37-Ubuntu SMP
 Fri Jun 11 07:54:58 UTC 2010
 i686
 GNU/Linux

Have looked on the V4L wiki :-[http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007](http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007)

This states that it should work, all be it, with a patch.

My computer doesn't seem to recognise the card;

```
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    Subsystem: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 8
    Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-via
    Kernel modules: via-agp

00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    Subsystem: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    Subsystem: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Kernel modules: via-agp

00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    Subsystem: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    Subsystem: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000cfff
    Memory behind bridge: efe00000-efefffff
    Prefetchable memory behind bridge: afd00000-efcfffff
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR+ <PERR-
    BridgeCtl: Parity+ SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel modules: shpchp

00:08.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
    Subsystem: Hauppauge computer works Inc. Device 6902
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (5000ns min, 13750ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx8800
    Kernel modules: cx8800

00:08.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
    Subsystem: Hauppauge computer works Inc. Device 6902
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (1000ns min, 63750ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx88_audio
    Kernel modules: cx88-alsa

00:08.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
    Subsystem: Hauppauge computer works Inc. Device 6902
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (1500ns min, 22000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx88-mpeg driver manager
    Kernel modules: cx8802

00:08.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
    Subsystem: Hauppauge computer works Inc. Device 6902
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (1500ns min, 63750ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 10
    Region 0: Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin B routed to IRQ 20
    Region 0: I/O ports at ec00 [size=8]
    Region 1: I/O ports at e880 [size=4]
    Region 2: I/O ports at e800 [size=8]
    Region 3: I/O ports at e480 [size=4]
    Region 4: I/O ports at e400 [size=16]
    Region 5: I/O ports at e000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sata_via
    Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 20
    Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    Region 4: I/O ports at fc00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via
    Kernel modules: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 21
    Region 4: I/O ports at dc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 21
    Region 4: I/O ports at d880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 21
    Region 4: I/O ports at d800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 21
    Region 4: I/O ports at d480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20)
    Subsystem: VIA Technologies, Inc. USB 2.0
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 128 bytes
    Interrupt: pin C routed to IRQ 21
    Region 0: Memory at f3fff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
    Subsystem: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
    Subsystem: Elitegroup Computer Systems Device aa01
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 22
    Region 0: I/O ports at d000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
    Subsystem: VIA Technologies, Inc. Device 0102
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (750ns min, 2000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 23
    Region 0: I/O ports at ee00 [size=256]
    Region 1: Memory at f3fff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
    Subsystem: PC Partner Limited Device 0200
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (2000ns min), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Region 1: I/O ports at c000 [size=256]
    Region 2: Memory at efef0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at efec0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon

01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
    Subsystem: PC Partner Limited Device 0201
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (2000ns min), Cache Line Size: 32 bytes
    Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Region 1: Memory at efee0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

```

Not really sure where to go/ what to do next.....

Any help gratefully received,

TIA Steve.

---

### Post by davidmohammed on 2010-07-24
you'll need to compile the v4l source code - taking the source code from the experimental branch rather than the standard V4l repository on their website - [http://linuxtv.org/hg]("http://linuxtv.org/hg")

Here is a link (post 15 onwards) which I described for someone how to compile the source code.  Note - you'll need to replace the repository name with the experimental branch...  There is a README on the above link that describes the different repositories

[http://ubuntuforums.org/showthread.php?t=1501570&page=2]("http://ubuntuforums.org/showthread.php?t=1501570&page=2").

After you've got a successful compile - you'll need to apply the patch to the source code and recompile.  When you've done this - run the make install 

...

and if all of that sounds intense - yes it is.  But in a strange way, that's the fun of compiling your own software!

---

### Post by bance on 2010-07-24
Thanks for the reply David, followed the various links......... Down loaded mercurial etc. etc.

When I go to /home/v4l-dvb/linux/drivers/media/saa7134/saa7134.h I find the already has an entry (it's marked as card 117)

This leaves me a bit stuck as to how to edit or modify as per the other posts!

forgive me if I'm being dim........

---

### Post by bance on 2010-07-25
Ok, so I've followed the procedures given in David's post all except modifing the code, which I don't think is neccesary since my card is listed!

When I called dmesg from terminal still not recognised.......

So I removed the other tuner card a Hauppage WinTV HVR 4000 and inserted the avermedia card in it's slot.

Now when dmesg is issued in terminal, the card is recognised, however the firmware fails to load,

The firmware file tda10046.fw is present in /lib/firmware, but the machine fails to load it. Is it possible to force the firmware to load?

TIA Steve,

---

### Post by davidmohammed on 2010-07-25
hi there,
  well done for compiling.

question - on the v4ll website - the avermedia card firmware is described as

dvb-usb-avertv-a800-02.fw	AVerMedia

is tda10046.fw the correct firmware?

or - one of the instructions state that you have to rename the firmware file to 

 /lib/firmware/dvb-fe-tda10046.fw

---

### Post by bance on 2010-07-25
Hi David,

Thanks for your help :D

I'm not sure where you've seen that firmware version  dvb-usb-avertv-a800-02.fw	AVerMedia,

I've been working from [this]("http://linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007") page, however I did notice in the dmesg output that the firmware revision differs from that shown!

---

### Post by davidmohammed on 2010-07-25
that link looks promising.  What firmware does dmesg say it requires?  Did you try renaming the firmware file you found to the name stated in the link?

---

### Post by bance on 2010-07-29
OK, managed to get the PC to recognise the card......

Used dvb-apps to scan for channels, made a channels.conf file and watched TV in Mplayer...... it works:p

Now I've reinstalled the other (hauppage) card, both cards are recognised but the tda1004x.fw file won't load correctly. I keep getting an error about the firmware version being incorrect. 

When I look in /lib/firmware I can only see 1 tda1004x.fw file and the properties don't give any version number.

Is there any way to check if there is more than one version of this file?

Or is it possible to force the loading of the correct file?

Once again THANK'S for the help.

Steve,

---

