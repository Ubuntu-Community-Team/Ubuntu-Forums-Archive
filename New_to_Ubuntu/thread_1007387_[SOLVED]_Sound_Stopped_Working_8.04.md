---
title: "[SOLVED] Sound Stopped Working? 8.04"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by mapes12 on 2008-12-10
Had sound working fine for ages on this Thinkpad T23 then yesterday I booted up the machine but no sound at all. There had been no configuration changes like updates or any new packages installed so I'm confused why there's no sound any more.

I've followed the advise on this thread [http://ubuntuforums.org/showthread.php?t=205449&page=2](http://ubuntuforums.org/showthread.php?t=205449&page=2) but no joy.

In Terminal ```
alsamixer
``` I get the following output > mark@ubuntu-laptop:~$ alsamixer
ALSA lib control.c:874: (snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory
mark@ubuntu-laptop:~$ 

```
aplay -l
``` throws out > mark@ubuntu-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mark@ubuntu-laptop:~$ 

Any help would be greatly appreciated.

---

### Post by fooman on 2008-12-10
have a look here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by mapes12 on 2008-12-10
> have a look here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)I have already tried that but it didn't work.

---

