---
title: "Alsa mixer u9.10 settings not saved"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by phaedr_os on 2009-11-09
I currently have onboard realtek sound chip which outputs to one internal speaker, front speakers, and rear speakers. The default speaker symbol on the top right only seems concerned with the internal speaker. Installing the gnome alsa mixer allows me to reduce the internal speaker volume and boost the front speakers' volume (to my amplifier) and thus work OK. BUT after switching off/rebooting, the next boot up of ubuntu has forgotten the mixer settings and sound comes mostly out of the internal speaker again.

How can the alsa mixer settings be saved for next time?

Regards

---

### Post by ~sHyLoCk~ on 2009-11-09
Type ```
alsamixer
``` in terminal and set your volumes and then:
```
sudo alsactl store
```

---

### Post by phaedr_os on 2009-11-10
Thanks but

sudo alsactl store

does not seem to be saving the mixer settings (or they are not being read after restart) - the internal speaker just jumps back up

This is a wubi install btw, but surely settings are saved the same as if a full linux install?

---

### Post by phaedr_os on 2009-11-24
The sound card is more controllable in kbuntu where the kde mixer is installed by default. Guess the real solution is to have gnome mixer installed by default in future

---

### Post by phaedr_os on 2009-11-26
I notice 'linuxwizard' has suggested:
 
>sudo alsactl store 0
 
(a slight difference) which i hope to try

---

### Post by orthopteroid on 2010-03-16
For me, ALSA was forgetting my line input setting upon reboot. After a boot amixer would show me:

Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'

So I ended up adding

amixer set 'Input Source' 'Line'

in my /etc/rc.local to force it to use the line input.

I'm a bit hazy on how 9.10 initializes alsa - for some reason alsa appears to be clobbering changes saved to the /var/lib/alsa/asound.state file.

---

