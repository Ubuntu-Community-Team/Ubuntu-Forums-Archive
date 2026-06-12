---
title: "Yesterday's update wiped out my sound, and changed my volume settings."
date: 2010-08-06
forum: New to Ubuntu
---

### Post by DesiArnez6 on 2010-08-06
Yesterday's update wiped out my sound, and changed my volume settings. I use Ubuntu 9.04, and I thought I used to see ALSA in the volume settings I now have my tabs separated into two "devices" and Pulse audio. There is no longer external nor internal sound.

This is my history of changes made to system, according to Synaptic History:
--------------------------------------------
Commit Log for Thu Aug 5 22:49:31 2010


Upgraded the following packages:
grub-common (1.96+20080724-12ubuntu2) to 1.96+20080724-12ubuntu2.1
grub-pc (1.96+20080724-12ubuntu2) to 1.96+20080724-12ubuntu2.1
libpcsclite1 (1.4.102-1ubuntu2) to 1.4.102-1ubuntu2.1
linux-headers-2.6.28-19 (2.6.28-19.61) to 2.6.28-19.62
linux-headers-2.6.28-19-generic (2.6.28-19.61) to 2.6.28-19.62
linux-image-2.6.28-19-generic (2.6.28-19.61) to 2.6.28-19.62
linux-libc-dev (2.6.28-19.61) to 2.6.28-19.62
---------------------------------------------

If somebody could help, I would really appreciate, as audio is my primary
use of my computer.

-Desi

---

### Post by nothingspecial on 2010-08-06
Does grub still list 2.6.28-19.61 as an option to boot.

If so (which it should) boot into that.

Don`t remove old kernels until you are sure the new one works

---

### Post by Zorgoth on 2010-08-06
Have you tried running alsamixer?

---

### Post by DesiArnez6 on 2010-08-06
> **Zorgoth said:**
> Have you tried running alsamixer?

I went to the Terminal and typed alsamixer, And it just said "cannot open mixer: No such file or directory"

Synaptic says, I have "alsa-utils" installed, but, "alsamixergui" and "gnome-alsamixer" are not installed according Synaptic

Thats how I run it right? just simply type alsamixer in the Terminal?

---

### Post by DesiArnez6 on 2010-08-06
> **nothingspecial said:**
> Does grub still list 2.6.28-19.61 as an option to boot.

If so (which it should) boot into that.

Don`t remove old kernels until you are sure the new one works

Yep, its the default for grub. I rebooted and still have no sound :(

---

### Post by DesiArnez6 on 2010-08-07
Been working on this all day, and Dell Ubuntu Support. They will call me tomorrow it seems, with a senior tech.

It seems as though the soundcard is not being properly recognized, that and the modules seem to be off? And I can't find the codec.

^This seems way over my head

---

### Post by nothingspecial on 2010-08-07
You haven`t posted your sound card
```

aplay -l
```

---

### Post by ravisghosh on 2010-08-11
I too got the exact same issue with Dell Studio 1555. Here is my aplay -l output:


> shantanu@GreenHead:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


---

### Post by DesiArnez6 on 2010-08-13
After trying nearly everything in the help section, I remembered that recently I had a similar problem  where I lost external sound, and decided to try what I'd done last time, but this time to restore external AND internal sound. This thread will show what I did:

[http://ubuntuforums.org/showthread.php?t=1533995](http://ubuntuforums.org/showthread.php?t=1533995)

---

### Post by lidex on 2010-08-13
> **DesiArnez6 said:**
> After trying nearly everything in the help section, I remembered that recently I had a similar problem  where I lost external sound, and decided to try what I'd done last time, but this time to restore external AND internal sound. This thread will show what I did:

[http://ubuntuforums.org/showthread.php?t=1533995](http://ubuntuforums.org/showthread.php?t=1533995)

You upgraded alsa for that fix and any kernel upgrade reverts you back to the stock version. Apparently you didn't look to closely at the alsa-upgrade thread-starter:
> Ubuntu upgrades/updates might overwrite your Alsa installation once in a while (e.g. Major upgrades, kernel-upgrades or ALSA-package upgrades).
You just need to rerun the upgrade-script using the -i option in this case (if you still have the compiled sources on the disk). 
And you **still** haven't marked that thread solved! :rolleyes:

---

