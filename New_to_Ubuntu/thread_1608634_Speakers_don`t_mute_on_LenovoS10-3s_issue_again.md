---
title: "Speakers don`t mute on LenovoS10-3s issue again"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by KarenJS on 2010-10-29
Hello all! Just bought Lenovo Ideapad S10-3s, installed Ubuntu 10.04 yesterday, updated just like EVERYTHING (so I`m running 2.6.32-25-generic), and stumbled upon bug [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/109838](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/109838) - the speakers won`t mute when I plug in the headphones.

I tried ALL the suggested solutions including the official solution ([https://wiki.ubuntu.com/Lenovo_S10-3t](https://wiki.ubuntu.com/Lenovo_S10-3t)) where I should add the 
```
options snd-hda-intel model="ideapad"
```at the end of /etc/modprobe.d/alsa-base.conf  

I managed it all just fine, rebooted like a million times, plugged and unplugged the headphones but the speakers are still on together with the headphones. Finally I re-read the LP bug solutions and downloaded [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/109838/+attachment/115869/+files/patch_realtek.c](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/109838/+attachment/115869/+files/patch_realtek.c) which is a patch file. Judging by what I found in the code - it IS just what I need to make the speakers mute. But I must admit I don`t know where to put this patch file. Please, help.

P.S. I read that this issue didn`t emerge under Karmic, so I ran Karmic-based MoonOS-3 in live mode, but got the same problem - the headphones and speakers worked simultaneously.

---

