---
title: "Upgraded to kernel 2.6.27-11 - creative X-fi not found"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by sproaty on 2009-01-28
steve@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
steve@ubuntu:~$ 

(that was on 2.6.27-11)

I've since rebooted, hit escape in the countdown before the system boots and chose to load the 2.6.27-9 kernel, and everything's fine, so I can definitely tell the kernel upgrade is to blame.

now:
steve@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: X-Fi 20k1 [WaveOut/WaveIn]
  Subdevices: 7/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
steve@ubuntu:~$ uname -a
Linux ubuntu 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

---

### Post by kansasnoob on 2009-01-28
I don't have an answer to the actual problem, but I've had similar problems with Kernel upgrades so I've found that "startupmanager" comes in handy until I find an answer and have time to deal with it.

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

That way you can keep booting the older kernel until you find the answer.

Wish I could actually be of more help.

---

### Post by kansasnoob on 2009-01-28
Just happened to think you may want to report this as a "bug"!

Good advice on that here:

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by sproaty on 2009-01-28
okay, I just reported it as a bug, hopefully other people will stumble across it

---

### Post by PhoenixP3K on 2009-01-29
Same problem here. I'll try loading older kernel to check.

---

### Post by rfbeck on 2009-02-07
Same thing here! Using old kernel to use my XFi.
______
Robert

---

