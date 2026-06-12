---
title: "Gnome Visual Effects and Graphics Card"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by llogan on 2009-02-11
Hi,

I am successfully running Intrepid (and loving it!).  I tried to bump up the visual effects on the Gnome desktop:  

System -> Preferences -> Appearance -> Visual Effects

By clicking on the Visual Effects tab, I discovered that my desktop visual effects were set to "None".  I then selected "Normal", it searched for drivers, the screen blinked a few times and then a dialog box came up saying "Desktop effects could not be enabled!"

I don't know whether this is because my on-board video just doesn't isn't powerful enough, or if my video isn't configured properly.  I am using PCI, not AGP.

sudo lspci -vv shows:

01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
	Subsystem: ASRock Incorporation Device 7205
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at d8000000 (32-bit, prefetchable) [size=64M]
	Region 1: Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Expansion ROM at dfef0000 [disabled] [size=64K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [70] AGP version 2.0
		Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2,x4
		Command: RQ=32 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x4

The above means absolutely nothing to me.  Can anyone tell me if I have the graphic capacity to enable Visual Effects ?

Thanks in advance...

---

### Post by nmccrina on 2009-02-11
According to this thread,

[http://ubuntuforums.org/showthread.php?t=184512&page=9]("http://ubuntuforums.org/showthread.php?t=184512&page=9")

it looks like that brand of card is inherently buggy. :(

---

### Post by RomeReactor on 2009-02-11
Hi. Most VIA integrated GPUs are very problematic regarding hardware acceleration in Linux in general; many won't give you direct rendering. I know this is not a solution, but if you definitely want desktop effects, you should try getting a dedicated nVidia or ATI card.

---

### Post by llogan on 2009-02-11
Hi,

Thanks for the speedy replies.  I looking at getting a refurbished GeForce mx 32mb AGP Pro for $20.  Would this make a significant difference to my graphical capabilities.  (I'm not a gamer.)

---

### Post by RomeReactor on 2009-02-11
I would suggest saving a little more so you can get either this [GeForce FX 5200]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130210") for $30 or this [GeForce 6200 256MB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814125249") for $40.

---

### Post by xbanex on 2009-02-11
Hi im also having the same issue  and i have an naivda fx 5600 i think

---

### Post by llogan on 2009-02-13
Thanks for all the great suggestions!  I'm finding this forum invaluable!

Llogan

---

### Post by zika on 2009-02-13
a shot in the dark. do You by any chance have "composition" enabled in metacity (=Normal)?
Alt-F2->gconf-editor->apps->metacity->general->uncheck (if checked)"compositing_manager"

---

### Post by llogan on 2009-02-13
Thanks for the suggestion.  No, it was not checked. It was worth a try though...

---

