---
title: "No Sound on Rig w/ Two Soundcards"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2009-06-17
I have an Asus A8N-VM CSM Motherboard with a PCI Creative SoundBlaster Audigy 2 soundcard in it. When i booted up my computer after work today there was no sound from both XP and Ubuntu, after testing the speakers through my ipod i ruled them out as the cuplrit.

I just reinstalled XP (as in, last night) so i'm not too worried about the lack of sound there (yet) but i run ubuntu about 99.9% of the time so i'd kind of like sound.

I had an issue before on another rig with an external soundcard and an internal one (that stopped working). apparently, the computer was seeing the internal one first, so even though it wasn't functional the computer used it as default. it was remedied by blacklisting the module for the internal card and rebooting.

except now, i don't know which is the proper module to blacklist. The nVidia MCP51 HDA card is the one i want to kill

```
rowdyp@nts-desktop:~$ lspci | grep udio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
04:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
```

```
rowdyp@nts-desktop:~$ lsmod | grep snd
snd_emu10k1_synth      14336  0 
snd_emux_synth         40832  1 snd_emu10k1_synth
snd_seq_virmidi        13440  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           144288  3 snd_emu10k1_synth
snd_ac97_codec        112292  1 snd_emu10k1
snd_hda_intel         435636  2 
ac97_bus                9856  1 snd_ac97_codec
snd_util_mem           12288  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15108  2 snd_emux_synth,snd_emu10k1
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     15104  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                56880  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14988  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  22 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16904  3 snd_emu10k1,snd_hda_intel,snd_pcm
soundcore              15200  1 snd
```

---

### Post by Don1500 on 2009-06-17
Go here, do what the man says. You will have music, and record it, too.


I have done this many times, and every time, it works.


[URL="http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html"]Click Here
[/URL]

---

### Post by Sonic Reducer on 2009-06-19
> **Don1500 said:**
> Go here, do what the man says. You will have music, and record it, too.


I have done this many times, and every time, it works.


[URL="http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html"]Click Here
[/URL]

i followed your guide, and i didn't get any sound until i clicked the checkbox in **Applications/Sound & Video/Volume Control/Switches/Audigy Analog-Digital Output Jack** and it started playing instantly. I'm using an el cheapo 2.1 system from wal-mart, definitely analog. i think my soundcard was trying to do SPDIF out and it simply wasn't working with my speakers.

also, when you turn your speakers up all the way to determine if they're not working or simply too quiet, **_REMEMBER TO TURN THEM DOWN_** or you'll give yourself a heart attack when you click a checkbox

---

### Post by Sonic Reducer on 2009-06-26
just a little update, i have no sound in flash and movie player (but VLC will play the same file with sound)

i already installed libgstreamer-plugins-base0.10-dev like the instructions said to, but i'm still not getting sound

---

