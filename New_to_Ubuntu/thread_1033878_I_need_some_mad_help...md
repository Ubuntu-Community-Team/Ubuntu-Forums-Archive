---
title: "I need some mad help.."
date: 2009-01-07
forum: New to Ubuntu
---

### Post by b00nz on 2009-01-07
Ok I'm quite new to Ubuntu. I know some commands and such, but still a newbie :(  Oh and I'm running Ubuntu 8.10

Anyway here is my issue. I know there is topics on this already and believe me when I say I've searched everywhere and none of them helped me. 

ISSUE: 

My sound is messing up. I've done the whole aoss, ALSA pulseaudio mumbo jumbo, and absolutely none of that stuf works. I even got my second sound blaster Live and now my sound is really jumbly and blotchy. It's like a guy getting electrocuted and trying to talk at the same time. I go into  my sound options and it's recognized.  

I have been wanting to play multiple sounds like for instance I'm a gamer and I understand all of Wine and all of that. I wouldn't be using Ubuntu if I couldn't play games :). But anyway I am in TeamSpeak and I can hear people and talk to people and then I go to say pandora to play some music, and nothing. No sound, not even a hesitation to play a sound. It's just silent. 

Like I said up there I have installed ALSA, the whole aoss thing done the whole start TS with the aoss infront of the name and then launch. I've done switching all of my sound to ALSA and then trying to run TS and other sounds. I don't know. 

My sound cars are: Sound Blaster LIVE! 
                   nVidia Corporation MCP61 High Definition Audio 

Please help me. Be kind to a nubzors :(

---

### Post by slibuntu on 2009-01-07
I know how frustrating sound issues are, so I'm bumping this for you!

All I can suggest is fiddling with alsamixer and the Sound Configuration gui. Failing that, I got so frustrated with my sound issues that I reinstalled, and it was fine all over again. A little OTT maybe, but did the trick

---

### Post by handydan918 on 2009-01-07
Let's start with some outputs.

Do 
```
lspci | grep -i audio
```

and ```
lsmod | grep -i snd
```

Let's see what you got.

---

### Post by atngplusultra on 2009-01-07
another good output to get is
```
aplay -l
```
because if nothing shows up there, then something is REALLY up.

---

### Post by b00nz on 2009-01-10
Thank you for the reply. To the first reply I have done all of the alsa mixer stuf. Nothing works but thanks. 

to handydan918: here is what i got..

lspci | grep -i audio
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
01:09.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X


 lsmod | grep -i snd
snd_usb_audio          89728  0 
snd_usb_lib            24192  1 snd_usb_audio
snd_hwdep              15236  1 snd_usb_audio
snd_hda_intel         381488  3 
snd_seq_dummy          10884  0 
snd_emu10k1x           24068  3 
snd_ac97_codec        111652  1 snd_emu10k1x
snd_seq_oss            38528  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  2 snd_pcm_oss
snd_pcm                83204  6 snd_usb_audio,snd_hda_intel,snd_emu10k1x,snd_ac97_codec,snd_pcm_oss
snd_seq_midi           14336  0 
ac97_bus                9856  1 snd_ac97_codec
snd_rawmidi            29824  3 snd_usb_lib,snd_emu10k1x,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  3 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  21 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_emu10k1x,snd_ac97_codec,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  2 snd
snd_page_alloc         16136  3 snd_hda_intel,snd_emu10k1x,snd_pcm
usbcore               148848  6 snd_usb_audio,snd_usb_lib,usbhid,ohci_hcd,ehci_hcd


I've been also trying to get my USB headset to work but with no luck STILL. 

and to atngplusultra

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
card 1: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [Microsoft LifeChat LX-3000 ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
aplay -l


There yall go. :)

---

### Post by sleepyjon on 2009-01-10
You said you get sound in TS. Do you get sound in other things when TS is not running? 

Don't just close TS and check, close TS and restart any programs that use sound.

---

### Post by b00nz on 2009-01-10
Well I don't get sound anymore to save my life. i've done every TUT i can find on how to get my sound working in TS. I got it to work one time but then i got to say [http://pandora.com](http://pandora.com) and i can't hear the music. 

After i installed ALSA i can't hear anything no one can hear me. I've tried Pulse Audio and that doesn't work.

---

### Post by handydan918 on 2009-01-10
If I read this correctly, you have two different sound cards, and my guess is that the nvidia is on-board. Assuming that to be the case, go into yoiur bios and disable the nvidia sound card. Then try the alsa stuff over for the soundblaster.

---

### Post by JoshuaRL on 2009-01-10
You may also have to add the driver for the onboard to the blacklist file.  Sometimes Linux ignores the BIOS settings (preferring instead to do its own hardware detection) and loads what it thinks you want.

---

