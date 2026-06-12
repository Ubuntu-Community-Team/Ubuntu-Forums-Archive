---
title: "ati sound and video?? i5 460m gpu?"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by adduds on 2011-02-25
Well first off i have an acer aspire 5820TG i5 460m and radeon 5650mobilty video card

Everyones really smart and helpful around here so i'm sure we'll get this solved :)

I feel that just default fresh install of ubuntu 10.10 i'm using my stock gpu because when i set up simple compiz and ultimate it can barely handle it and doing a video stress test in win7 on counterstrike i get like 120fps 

Honestly i'm soooo confused i went through the binary driver how to downloaded the "sudo sh ati-driver-installer-11-2-x86.x86_64.run --buildpkg Ubuntu/maverick"

and installed all the .debs even when i lpsci it shows kernal driver in use is fglrx_pci....:'( i just got this laptop n really hope this all works out...

can i do a video stress test or find out conclusively which gpu i'm using??

Problem 1:

When i install flgrx and reboot it just brings me to a command line to login login..?

i booted into safe mode and ran flgrxinfo and got:

```
toews@kidlapp:~$ fglrxinfo 
X Error of failed request:  BadRequest (invalid request code or no such operation)[/URL]
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
toews@kidlapp:~$ sudo aticonfig --initial
Found fglrx primary device section
 Unable to find any supported Screen sections
toews@kidlapp:~$ fglrxinfo 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

> toews@kidlapp:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
	Subsystem: Acer Incorporated [ALI] Device 035d
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 **VGA** compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 035d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 44
	Region 0: Memory at d8000000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 4050 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:1b.0 **Audio device**: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 035d
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 45
	Region 0: Memory at dc500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 035d
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at dc504000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: intel ips
	Kernel modules: intel_ips

01:00.0 **VGA** compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 035d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d0000000 (64-bit, prefetchable) [size=128M]
	Region 2: Memory at dc400000 (64-bit, non-prefetchable) [size=128K]
	Region 4: I/O ports at 3000 [size=256]
	Expansion ROM at dc440000 [disabled] [size=128K]
	Capabilities: <access denied>
[B]	Kernel driver in use: fglrx_pci
	Kernel modules: radeon[/B]

01:00.**1 Audio device**: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
	Subsystem: Acer Incorporated [ALI] Device 035d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 46
	Region 0: Memory at dc420000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel




Second issue:

I have the option for two audio outputs internal audio and redwood HDMI audio when i select redwood and test speaks i get bupkiss

Screenshot for audio:

[http://img225.imageshack.us/img225/4801/soundprob.png](http://img225.imageshack.us/img225/4801/soundprob.png)

it seems like all the onboard stuff is being used and my ati stuff isn't...

> toews@kidlapp:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC271X Analog [ALC271X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC271X Digital [ALC271X Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



Screenshot for video:

[[IMG]http://img197.imageshack.us/img197/8138/atiissue.jpg[/IMG]](http://img197.imageshack.us/i/atiissue.jpg/)


EDIT: i ran glxgears?!?!?! i got 50-60 fps wtf?! is says it should be approx same as moniter refresh??

toews@kidlapp:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.304 FPS
300 frames in 5.0 seconds = 59.872 FPS
301 frames in 5.0 seconds = 60.073 FPS
300 frames in 5.0 seconds = 59.872 FPS
301 frames in 5.0 seconds = 60.073 FPS
257 frames in 5.0 seconds = 51.290 FPS

---

### Post by adduds on 2011-02-26
le bump

---

