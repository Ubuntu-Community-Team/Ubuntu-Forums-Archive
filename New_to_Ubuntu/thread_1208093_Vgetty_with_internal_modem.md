---
title: "Vgetty with internal modem"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by hannaman on 2009-07-08
I have a server running Jaunty server edition that I want to use as a voicemail server.  I have installed mgetty-voice, but I cannot get it to see my internal modem.  When I run minicom, it doesn't initialise the modem no matter what /dev/tty setting I use.

Here is the output of lspsi -vv

```
06:01.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
	Subsystem: Agere Systems Device 044c
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (63000ns min, 3500ns max)
	Interrupt: pin A routed to IRQ 3
	Region 0: Memory at ff503400 (32-bit, non-prefetchable) [size=256]
	Region 1: I/O ports at bc00 [size=8]
	Region 2: I/O ports at b800 [size=256]
	Capabilities: [f8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=160mA PME(D0-,D1-,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```

The output of the scanModem script from linModems just tells me that USB modem not detected by lsusb, but since it is a pci modem that should be expected.

hwinfo --modem just exits and doesn't return anything.

I am not sure where to go from here.  Does anyone have any experience with using an internal pci voice/data/fax modem for a voicemail server?

---

