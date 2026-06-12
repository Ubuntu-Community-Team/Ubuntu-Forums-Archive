---
title: "sound volume too low"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by paker on 2009-02-21
My new build is working well except for sound. It is extremely low, not cracking or anything.

1) I tried different players. Same result.
2) Set volume at max from Speaker icon > open volume control. no change.
3) Changed Auto to ALSA in System > Preferences > Sound. No change.
4) switched to different headphones. no change.

My system:

Intel Q9330
Gigabyte GA-EP45-UD3R
onboard sound
ubuntu 8.10 32 bit

Thanks.

---

### Post by mc4100 on 2009-02-21
Have you tried raising the PCM?
```
alsamixer -Dhw
```

---

### Post by paker on 2009-02-21
PCM is already at max from:

Speaker icon > PCM > Raise bar.

---

### Post by paker on 2009-02-21
Problem solved. 

Problem: Intel ICH10-based HD Audio (my onboard audio) is not supported by the ALSA in the repository. Volume is way too low.

Solution: Upgrade to the current version of ALSA.

How to: [http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade](http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade). Get the upgrade script "AlsaUpgrade-1.0.x-rev-1.16.tar" from the thread and install. 

tar xvf AlsaUpgrade-1.0.x-rev-1.16.tar
sudo ./AlsaUpgrade-1.0.x-rev-1.16.sh -di

Note: -di is for downloading and installing. Reboot.

---

### Post by auntiestacey on 2009-02-21
Thanks paker for the post. I've had the same problem since installing this week. Will try this when I get home from work.

---

### Post by paker on 2009-02-21
> **auntiestacey said:**
> Thanks paker for the post. I've had the same problem since installing this week. Will try this when I get home from work.In case you are as unskilled as me, 

tar xvf AlsaUpgrade-1.0.x-rev-1.16.tar

This converts "xxx.tar" to "xxx.sh" and stores it in the home folder.

sudo ./AlsaUpgrade-1.0.x-rev-1.16.sh -di

This downloads and installs newer ALSA per "xxx.sh."

---

### Post by auntiestacey on 2009-02-22
Unfortunately sound didn't change with the update. I have Realtek ALC888 integrated sound on my nvidia 8200 mobo.

I found this  post on Linux forums and will try this next. Posting here for others in the same boat with me.

[http://www.linuxforums.org/forum/ubuntu-help/100864-realtek-hd-audio-alc888.html](http://www.linuxforums.org/forum/ubuntu-help/100864-realtek-hd-audio-alc888.html)

-as

---

