---
title: "I'm deaf!!"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by calisoca on 2008-12-12
I've searched and searched, and I cannot find a solution to my problem.  It seems simple enough.

I have installed Ubuntu 8.10, and no sound will play.

This seems like a common problem, yet I haven't been able to fix it!  

I'm a new to Linux, so I was wondering if there was anyway someone might be able to help.  I'd greatly appreciate it!

I've already run alsamixer, and it allowed me to change the volume setting.  I ensured that the volume was set at max.

THE RESULTS OF "aplay -l":
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

THE RESULTS OF "lspci -v":
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by SuperSonic4 on 2008-12-12
what filetypes are you trying to play? The following is adapted from the arch wiki

```
sudo apt-get alsa-utils
```
```
alsamixer
```

and have you ensured they are not muted? (I think it has MM if they are not muted)

```
aplay <path to sound file>
```

---

### Post by sneeks on 2008-12-12
also check your sound in preferences,and make sure its not muted there,and uncheck the headphone thinngy....

---

### Post by calisoca on 2008-12-12
Yep, I've doubled checked to make sure the sound is not muted.

How do I check my sound in preferences, and how do I un-check the headphone option; although, when I plug in headphones, I still can't hear anything.

---

### Post by calisoca on 2008-12-12
Okay, I've made sure that all the volume levels in the ALSA MIXER were turned all the way up.

However, there are two that I can't change.

IEC958 and IEC958 D are turned all the way down, and I can't change those.

Anyway, I've still made no progress.

---

### Post by kansasnoob on 2008-12-12
Try installing gnome-alsamixer. Since you're new it's best to use synaptic. It'll then show up in Sound & Video. Then pay special attention to the first three and last four (via) toggles.

You can also install it from terminal:

```
sudo apt-get install gnome-alsamixer
```

---

### Post by markbuntu on 2008-12-12
Try this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that does not help go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by sstusick on 2008-12-12
Try killing Pulse Audio. Whenever I've had troubles with sound, Pulse Audio was usually the culprit.

---

### Post by calisoca on 2008-12-12
Holy crap!  FINALLY!!!  It works.

I uninstalled PulseAudio, and then I changed everything in my sound preferences to HDA Intel CONEXANT Analog (OSS).

Suddenly, it now works.

Thanks everyone for the help!

---

### Post by sstusick on 2008-12-12
You're welcome. Be sure to mark this thread as solved, then ;)

---

