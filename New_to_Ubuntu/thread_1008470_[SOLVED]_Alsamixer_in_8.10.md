---
title: "[SOLVED] Alsamixer in 8.10?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by mapes12 on 2008-12-11
Screwed my sound up in 8.04 so decided to do a fresh install of 8.10 on this Thinkpad T23. Partitions are:

sda1 - /
sda3 - /home
sda5 - Swap

Installed 8.10 from a live CD. At the partitioning stage I edited the configuration to _format_ sda1 and install "/" 

sda3 and sda5 were edited to be used as /home and swap respectively but not formatted. All went well. Install went fine with all personal settings and files preserved.

However, sound still does not work. In Terminal ```
alsamixer
```brings up the attached thumbnail. As you can see Card and Chip are labelled PulseAudio but at the top the label is Alsamixer v1.0.17

Would I be right to assume that 8.10 now uses PulseAudio. If so why is the top label still Alsamixer? And given that I have retained my previous /home is this something to do with why sound still doesn't work??

I've been grappling with this for 2 days now and it's driving me nuts.

---

### Post by halitech on 2008-12-11
its showing alsamixer because that is what you ran. in a terminal, post the output of
```
aplay -l
```

---

### Post by mapes12 on 2008-12-11
Here we go > mark@ubuntu-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mark@ubuntu-laptop:~$ 

---

### Post by halitech on 2008-12-11
try this in a terminal
```
sudo asoundconf set-default-card ICH3
```
might need to reboot to get it to work

---

### Post by mapes12 on 2008-12-11
> **halitech said:**
> try this in a terminal
```
sudo asoundconf set-default-card ICH3
```
might need to reboot to get it to workDid that and reboot but still no sound:confused:

---

### Post by halitech on 2008-12-11
do you have a set of external speakers or headphones? maybe its outputting to them instead of your built in speakers.

---

### Post by mapes12 on 2008-12-11
> **halitech said:**
> do you have a set of external speakers or headphones? maybe its outputting to them instead of your built in speakers.Known working headphones hooked up but still no sound:confused:

---

