---
title: "&quot;.asoundrc&quot; file for Ubuntu 9.04, dmix + optical (iec958) sound"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by LeDechaine on 2010-05-03
Pissed off of searching...

According to the official ALSA wiki, what I need to do to use dmix, is create a **.asoundrc** file like this.

```
pcm.!default {
	type plug
	slave.pcm "dmixer"
}

pcm.dmixer  {
 	type dmix
 	ipc_key 1024
 	slave {
		pcm "**iec958:Audigy2**"
		period_time 0
		period_size 1024
		buffer_size 4096
		rate 44100
	}
	bindings {
		0 0
		1 1
	}
}

ctl.dmixer {
	type **iec958**
	card **Audigy2**
}
```

But I just can't. "**dmix plugin can be only connected to hw plugin**".
I'm using **iec958:Audigy2**, because **aplay -l** DOESN'T tell me where is the digital output. Only **aplay -L** does.

```
$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: Audigy2 [Audigy 2 ZS [2001]], périphérique 0 : emu10k1 [ADC Capture/Standard PCM Playback]
  Sous-périphériques: 32/32
  Sous-périphérique: #0: subdevice #0
  Sous-périphérique: #1: subdevice #1
  Sous-périphérique: #2: subdevice #2
  Sous-périphérique: #3: subdevice #3
  Sous-périphérique: #4: subdevice #4
  Sous-périphérique: #5: subdevice #5
  Sous-périphérique: #6: subdevice #6
  Sous-périphérique: #7: subdevice #7
  Sous-périphérique: #8: subdevice #8
  Sous-périphérique: #9: subdevice #9
  Sous-périphérique: #10: subdevice #10
  Sous-périphérique: #11: subdevice #11
  Sous-périphérique: #12: subdevice #12
  Sous-périphérique: #13: subdevice #13
  Sous-périphérique: #14: subdevice #14
  Sous-périphérique: #15: subdevice #15
  Sous-périphérique: #16: subdevice #16
  Sous-périphérique: #17: subdevice #17
  Sous-périphérique: #18: subdevice #18
  Sous-périphérique: #19: subdevice #19
  Sous-périphérique: #20: subdevice #20
  Sous-périphérique: #21: subdevice #21
  Sous-périphérique: #22: subdevice #22
  Sous-périphérique: #23: subdevice #23
  Sous-périphérique: #24: subdevice #24
  Sous-périphérique: #25: subdevice #25
  Sous-périphérique: #26: subdevice #26
  Sous-périphérique: #27: subdevice #27
  Sous-périphérique: #28: subdevice #28
  Sous-périphérique: #29: subdevice #29
  Sous-périphérique: #30: subdevice #30
  Sous-périphérique: #31: subdevice #31
carte  0: Audigy2 [Audigy 2 ZS [2001]], périphérique 2 : emu10k1 efx [Multichannel Capture/PT Playback]
  Sous-périphériques: 8/8
  Sous-périphérique: #0: subdevice #0
  Sous-périphérique: #1: subdevice #1
  Sous-périphérique: #2: subdevice #2
  Sous-périphérique: #3: subdevice #3
  Sous-périphérique: #4: subdevice #4
  Sous-périphérique: #5: subdevice #5
  Sous-périphérique: #6: subdevice #6
  Sous-périphérique: #7: subdevice #7
carte  0: Audigy2 [Audigy 2 ZS [2001]], périphérique 3 : emu10k1 [Multichannel Playback]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Audigy2 [Audigy 2 ZS [2001]], périphérique 4 : p16v [p16v]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
```

```
$ aplay -L
front:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
side:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    Side speakers
surround40:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
[B]iec958:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output[/B]
null
    Discard all samples (playback) or generate zero samples (capture)
```

Tell me what to write in this .asoundrc file. Thanks.

---

### Post by afrodeity on 2010-07-03
bump

---

