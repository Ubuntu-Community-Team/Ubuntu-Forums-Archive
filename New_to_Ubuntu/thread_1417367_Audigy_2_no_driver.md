---
title: "Audigy 2 no driver"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Kerkyros on 2010-02-27
Hello, I've got a question on where to get driver for my Audigy 2 sound card for Ubuntu 8.04.

---

### Post by Kerkyros on 2010-02-27
Refresh, does anybody know a tutorial or sth on installing driver for Audigy 2?
Still no idea where to get it

---

### Post by gvoima on 2010-02-27
For me audigy 2 zs worked out of the box.
Are you sure your card isn't installed or you just don't get any sound?
```
lsmod | grep emu10k
```
Type this into console, what is the output?

---

### Post by Kerkyros on 2010-02-27
That's the output:
```
snd_emu10k1_synth       8064  0 
snd_emux_synth         36224  1 snd_emu10k1_synth
snd_emu10k1           146880  3 snd_emu10k1_synth
snd_util_mem            5632  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10500  2 snd_emux_synth,snd_emu10k1
snd_ac97_codec        101028  2 snd_emu10k1,snd_via82xx
snd_pcm                78596  4 snd_emu10k1,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  3 snd_emu10k1,snd_via82xx,snd_pcm
snd_rawmidi            25760  4 snd_seq_virmidi,snd_emu10k1,snd_mpu401_uart,snd_seq_midi
snd_timer              24836  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9612  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
emu10k1_gp              4608  0 
snd                    56996  27 snd_mpu401,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hwdep,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq_dummy,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
gameport               16008  4 analog,snd_via82xx,emu10k1_gp

```

---

### Post by gvoima on 2010-02-27
ok, so your soundcard modules is loaded and should be working. Next is to check if there is some mute's on any channels.
Because it is a alsa driven soundcard, use **alsamixer** (in console) to check if there is volume in atleast PCM and Master channel and nothing is on mute.
Try to adjust also the other channels and see if that helps.

---

### Post by Kerkyros on 2010-02-27
Alsamixer says that card used is:
[AlsaMixer v1.0.15 (Press Escape to quit)
&#9474; Card: VIA 8235                                                  
&#9474; Chip: Realtek ALC655 rev 0  
So the onboard card, how to change preferred device to Audigy2 ?

---

### Post by gvoima on 2010-02-27
Ohh...
Well you should disable the onboard card from the BIOS.
And you can change the card you use from the sound manager.

I'm not sure did 8.04 use pulseaudio or the older sound manager, but you can right-click on the speaker icon on notification area and select properties.

There should be a dropdown box from which you can select what card and what channel is used atm.
e.g. Audigy 2 and Master.

I'm not 100% sure, because it has been a while when I used 8.04.
hope this helps some..

A sure bet would be to disable the onboard card from bios if it is not needed. The module for it would be automaticly unloaded at startup and audigy used instead.

---

### Post by impert on 2010-02-27
Kerkyros, the best thing to do is to go through the steps in this [thread]("http://http://ubuntuforums.org/showthread.php?t=205449"):

My guess is that you can probably use the ca0106 module (snd-ca0106) with that card, but I could be wrong. If alsa insists on  using the on-board sound card you may have to add
options snd-ca0106 index=0
at the end of your /etc/modprobe.d/alsa-base.conf file.

---

### Post by Kerkyros on 2010-02-28
impert & gvoima - thank You very much, now the card works perfectly :)

---

