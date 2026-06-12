---
title: "No Sound"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by rosehipzero on 2010-09-11
I installed Ubuntu 10.04 on this new rig and i have neither sound nor wireless connectiveity (the latter isnt too important). I have an ASUS M4A87TD EVO. I've never had issues with sound in the past so this is entirely new to me -_-

Also, wireless adapter is my old Linksys WMP300N. I tried Ndiswrapper and both broadcom drivers and nothing. However, this issue isnt that bad since i can just pull out the ethernet cable when i feel like using Ubuntu over Win7 for now... No wireless is a hindrance though but not too important. I would prefer the sound to be fixed over this!

---

### Post by jtarin on 2010-09-11
Menu>System>Administration>Sound...check your output volume, make sure mute is unchecked.If this doesn't do it tell us what you have done to try and restore sound?

---

### Post by rosehipzero on 2010-09-11
Mute was the first thing i checked. I also checked that the speakers were working, plug into the right socket and correct codecs were installed to play my music. 

Also, there isnt any sound at boot. And i havent tried anything technical since i've never had this issue before and dont really know. I did a few google searches and nothing specific to my motherboard.

---

### Post by jtarin on 2010-09-11
If you are comfortable using the terminal enter the command```
lspci |grep Audio
```post the output.Then the command ```
lsmod |grep snd
```post the output.

---

### Post by rosehipzero on 2010-09-11
I use terminal daily ^_~ 

as for the first output: 
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
```

Second output
```
snd_hda_codec_via      33207  0 
snd_usb_audio          92747  1 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_hda_intel          25677  6 
snd_hda_codec          85759  2 snd_hda_codec_via,snd_hda_intel
snd_pcm                87882  5 snd_usb_audio,snd_pcm_oss,snd_hda_intel,snd_hda_codec
snd_usb_lib            19193  1 snd_usb_audio
snd_seq_dummy           1782  0 
snd_hwdep               6924  2 snd_usb_audio,snd_hda_codec
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71106  25 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm

```

---

### Post by rosehipzero on 2010-09-11
I got sound to work from the front panel audio jack, but doesnt work from the motherboard panel. It'll have to make do since i dont really wanna play with it too much...

I guess this is solved...?

---

### Post by jtarin on 2010-09-11
In the terminal```
alsamixer
```adjust levels.

---

### Post by kyrandesa on 2010-10-29
I've got the same problem: 
On the front output I get sound (if I put all of the mixers to max.), but on the motherboard output I don't get anything.

And i've just exchanged the motherboard, so sound has worked before quite satisfyingly. Any ideas? I've heard rumors that it might be due to a too old ALSA version?

The outputs: 

```
# lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
04:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
# lsmod | grep snd
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_via      33207  0 
snd_pcm_oss            41394  0 
snd_hda_intel          25773  1 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel
snd_mixer_oss          16299  1 snd_pcm_oss
snd_hwdep               6924  1 snd_hda_codec
snd_pcm                87946  3 snd_pcm_oss,snd_hda_intel,snd_hda_codec
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71251  13 snd_pcm_oss,snd_hda_intel,snd_hda_codec,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
```

---

### Post by rosehipzero on 2010-11-09
> **jtarin said:**
> In the terminal```
alsamixer
```adjust levels.

that worked! thanks

---

### Post by kyrandesa on 2010-11-09
Update: i upgraded to 10.10 and there the sound works normally again. 

Having sound from the front panel outlet was just not acceptable.

---

### Post by rosehipzero on 2010-11-10
yeah, it feels great to have it working!

---

