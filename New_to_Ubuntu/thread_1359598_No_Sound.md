---
title: "No Sound"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Xoanan on 2009-12-19
Hi All

I just recently got another pc from my Brother in Law; I installed xubuntu on it, but I am not getting any sound.  I believe I have it connected properly.  Any thoughts?

```
02:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs Device 0058
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at dc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1
```

---

### Post by Xoanan on 2009-12-20
```
xoanan@ubuntu:~$ lsmod | grep snd
snd_emu10k1_synth      14464  0 
snd_emux_synth         41472  1 snd_emu10k1_synth
snd_seq_virmidi        13568  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           145696  2 snd_emu10k1_synth
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
snd                    63396  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd


```

---

### Post by Roger Allott on 2009-12-20
Open your Hardware Drivers screen and if you see a 'Software Modem' installed, remove it and reboot.

---

### Post by Xoanan on 2009-12-20
Nope; just NVidia

---

### Post by Gtklocker on 2009-12-20
Open a terminal and write:

alsaconf
alsamixer

______________________________

It might be an XFCE sound applet problem. Try to:

apt-get install gstreamer-*

---

### Post by joes7 on 2009-12-20
Re-install your speakers.

---

### Post by Xoanan on 2009-12-20
Found the issue! Apparently if you use the Audigy Analog/Digital Output Jack in the Alsa Mixer, you get a lot of feedback.  I turned it off, made sure I placed the plugs in the right place and I am rocking and rolling!!:popcorn:

Thanx!!:guitar:

---

