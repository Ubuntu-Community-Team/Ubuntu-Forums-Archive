---
title: "snap, crackle, pop: curious sound recording problem"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by relic70 on 2009-01-08
The Rice Crispies sounds are the only sounds I could think of to describe the popping, crackling, popping, or static I hear when I record audio through Gnome Sound Recorder or Audacity.

I recently installed Intrepid and configured the Pulse Audio as per psyke83

[URL="http://ubuntuforums.org/showthread.php?t=789578"]

Playback of sound is not a problem. Playback of CDs, streaming internet audio (Pandora, PBS, and so forth) is perfect. No Snap, Crackle, Pop as I listen to these playbacks. 

The psyke83 post of Pulse Audio said little about recording audio. I've tried many combinations of settings on the pulse audio recording and playback levels thru the volume control of pulse audio and that of the sound icon on the panel. No matter what levels I set for playback, recording, input, etc. It doesn't matter. I still get the static or popping, crackling on playback of the recording.

With my previous installation of Hardy the recordings of audio with Sound Recorder or Audacity were perfect. No popping or static sounds.

My question is - What happened?

Here is the information from

 aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

AND FROM

 lspci -vv


02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X 
	Subsystem: Creative Labs Device 1003 
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 64 (500ns min, 5000ns max) 
	Interrupt: pin A routed to IRQ 17 
	Region 0: I/O ports at df20 [size=32] 
	Capabilities: <access denied> 
	Kernel driver in use: EMU10K1X 
	Kernel modules: snd-emu10k1x 

Thanks for any hints or advice

---

### Post by stanz on 2009-01-10
I disabled the 'switch' *SBLive Analog/Digital Output Jack* in my sound preferences.
Something automatically done - I didn't check it.

Help any?

---

### Post by relic70 on 2009-01-10
> **stanz said:**
> I disabled the 'switch' *SBLive Analog/Digital Output Jack* in my sound preferences.
Something automatically done - I didn't check it.

Help any?

The Analog/Digital Output Jack switch was not active and it was muted when I looked at the settings from the

alsamixer -Dhw

window.

So, it appears that's not the problem. The static in the background still exits, even though the audio itself is quite clear.

No Joy!

---

### Post by relic70 on 2009-01-13
FYI:

I gave up. Tried every conceivable type of sound settings in Intrepid and still no luck with getting rid of that background interference.

Went back to a new Hardy install (pain in the neck - lots of apps to reinstall).

BUT - now records again as in the previous Hardy install with no problems with background snap, crackle, pop, or static on the recordings.

---

