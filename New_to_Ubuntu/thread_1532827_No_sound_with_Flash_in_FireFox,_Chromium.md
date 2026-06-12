---
title: "No sound with Flash in FireFox, Chromium"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by sleepee on 2010-07-17
OK.  I've been rattling my brains trying to figure out a series of sound issues i've been having lately.
it all started when i realized my laptop speakers don't mute when i insert headphones.  no big deal, this happened to me before in 9.10 (i'm using lucid now) and all i had to do was upgrade alsa... so that's what i did.
after that it's been all downhill.

the jack sensing was fixed, but i had some other weird problems that i fixed (i think) by just messing around with pulse audio sound preferences and volume controls..  it was really weird, because the audio from all my applications would play perfectly for a while, but after a few minutes, everything would stop playing and i'd get no sound from any application.... but for some reason, when i ran aplay to test my audio, it would work...  anyway, that's fixed... sort of..

the problem is, even though i finally now have sound working with totem, vlc, etc., the one thing that is missing is sound from flash in Firefox and Chromium.  The video works fine and plays normally, but i can't hear anything from flash audio.
what really boggles my mind is that Flash works perfectly in Opera, with sound and everything.
So my head hurts too much right now to even think about what could be wrong now, so i turn to any of you fine ubuntu/linux experts yet again for advice.

anyway, here's some of the info i know i'm going to get asked for.

```
sleepee@sleepee-laptop:/usr/lib/flashplugin-installer$ uname -a
Linux sleepee-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

```

```
sleepee@sleepee-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Thanks in advance

---

### Post by bprins on 2010-08-10
not sure if this solves the problem you run in to, but:
1) aplay -l lists 4 hdmi devices. problem is that alsa doesnt mask correctly. adapt your sound.conf (file probably doesnt exist yet, if so, then create it)

```

bas@ubuntu-lt:~$ cat /etc/modprobe.d/sound.conf
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel enable_msi=0 probe_mask=-1,4

```

after you changed sound.conf, reboot and verify that you have 1 hdmi device now.

2) the problem that flash doesnt output sound lies within your aplay devices. you can change the order of devices listed in aplay. more on that topic if you still have a problem can be found here:

[http://www.nvnews.net/vbulletin/showthread.php?p=2198909](http://www.nvnews.net/vbulletin/showthread.php?p=2198909)

Hope this helps. Good luck.

---

### Post by sleepee on 2010-09-18
yea, i don't remember how i fixed this problem, but i fixed it a while ago...
sorry about that...

---

