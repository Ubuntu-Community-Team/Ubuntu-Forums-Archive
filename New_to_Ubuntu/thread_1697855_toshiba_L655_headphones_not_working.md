---
title: "toshiba L655 headphones not working"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by bmx391xmb on 2011-03-01
I'm running ubuntu 10.10 on a toshiba L655-S5111. when I plug working headphones  into the jack I get no sound out of them and the sounds continue to play through the on board speakers. I've searched the forums as well as google and found no solutions (new to linux btw). headphones dont show up in the alsamixer and the whole "change output" option isnt there in sound preferences. I do have pulseaudio volume control installed and it doesn't seem to have any options to tweak and fix this either. it seems like linux doesnt recognize the jack at all. can anyone please help?

---

### Post by komputes on 2011-03-01
I found the following workaround, although it is may not be an exact match with your hardware. For this reason I would ask that you first paste the output of the following two commands:

```
$ cat /proc/asound/card*/codec#* 2>/dev/null | grep Codec
$ lspci -nnk | awk 'BEGIN {x=0; IGNORECASE=1}; /^[^\t]/ {x=0}; /udio/ {x=1}; x == 1 {print}'
```

> I was able to get all the audio issues fixed by adding "options snd-hda-intel model=thinkpad" to /etc/modprobe.d/alsa-base.conf

Source: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/680844/comments/5](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/680844/comments/5)

---

### Post by bmx391xmb on 2011-03-01
Codec: Conexant CX20585
Codec: ATI R6xx HDMI










00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:fd50]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
01:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
	Subsystem: Toshiba America Info Systems Device [1179:fd50]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

