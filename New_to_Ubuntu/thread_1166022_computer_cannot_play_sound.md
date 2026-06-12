---
title: "computer cannot play sound"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by akimatsu123 on 2009-05-21
Hi,

I own an Lenovo X200 Tablet. I installed my OS yesterday. I am sure the sound was working fine when i first installed. 

Then I installed some packages (a lot of them), updated, and configured the lenovo active protection system for my hard disk. 

now the sound does not work. i can control the volume, but whenever a sound is supposed to play it makes a sound that sounds like static on the radio. i've already gone under system --> preferences --> sound and tried every single driver, but it doesn't seem to fix the problem. 

Any ideas?

Here is my audio section for lspci -vv if it helps:

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo Device 20f2
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at f2920000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```



Thanks

---

