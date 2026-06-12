---
title: "Sound not working."
date: 2010-04-01
forum: New to Ubuntu
---

### Post by Talkie_Toaster on 2010-04-01
Hey, I've recently installed Ubuntu 9.10 using wubi. Everything seems OK, except whatever I do I can't get any sound. I've already tried a suggestion in a generic thread suggesting I type [FONT=monospace]aplay -l[/FONT], which gives[FONT=monospace] [COLOR=black]
[/COLOR]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Which suggests everything is fine, according to that thread. Next I tried following the instructions [here]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"), and to be honest for the [alsa upgrade]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/") suggested I simply copied and pasted code to the terminal. Seemed to have no effect at all. I've also tried putting everything on full in alsamixer. Anyone got any ideas?
[/FONT]

---

### Post by GepettoBR on 2010-04-01
This may sound dumb, but did you log off, then log in again? Certain changes to ALSA settings only take effect the next time you log in.

---

### Post by Talkie_Toaster on 2010-04-01
> **GepettoBR said:**
> This may sound dumb, but did you log off, then log in again? Certain changes to ALSA settings only take effect the next time you log in.
Yeah, I restarted straight after, still no luck.

---

### Post by GepettoBR on 2010-04-01
For some reason the link to your alsa upgrade page isn't loading right now. I have the same sound card as you and it works OOTB in Karmic.

Can you post the output of running ```
lsmod | grep snd
``` in a Terminal?

---

