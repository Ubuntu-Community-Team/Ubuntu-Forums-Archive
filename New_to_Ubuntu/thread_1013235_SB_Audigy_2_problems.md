---
title: "SB Audigy 2 problems"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by rdecarlo on 2008-12-16
I just finished reinstalling Ubuntu and my Audigy 2 stopped working in Ubuntu.  The card is an Audigy 2 but gets mistakenly identified as an Audigy Platinum.  The onboard sound is disabled in the bios and I even tried blacklisting the onboard sound but I still get no sound.

 sudo lsmod | grep snd

snd_emu10k1_synth      14464  0 
snd_emux_synth         41344  1 snd_emu10k1_synth
snd_seq_virmidi        13568  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           146208  5 snd_emu10k1_synth
snd_ac97_codec        111652  1 snd_emu10k1
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  2 snd_emu10k1,snd_pcm
snd_util_mem           12416  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15236  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     15232  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                57776  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         15116  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  21 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd

Any suggestions?

---

### Post by Therion on 2008-12-16
Do you know how to disable the Audigy Analog/Digital Output Jack?  That might get you jump started.  
I can't remember the navigation and I'm stuck behind an XP machine at work ATM...

Whoopsie... This assumes you're running 8.04 or prior.  Probably does not apply to 8.10

---

### Post by rdecarlo on 2008-12-16
I pulled up the mixer and disabled it.  I tried it with it both on and off.  Turning the digital output on just sent some noise to my speaker.  Could the problem be that I have a plain Audigy 2 and Ubuntu thinks that it is an Audigy 2 Platinum?  It seems like I should get some sound anyway.

---

### Post by Therion on 2008-12-16
Hmmmm... Okay.

Check under File -> Change Device and see if you can change the chosen soundcard.  

I would think that, yes, you should be getting some kind of sound even if the exact ID of your card is a little off.

---

