---
title: "Newbie in need of help with sound"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Katmai on 2009-02-14
Hello mates,

First of all i want to thank everybody for the valuable support that you offer for everyone who tries to escape from Windows!I used to have ubuntu on my Office PC and everything works fine there. But recently i felt like making another step and install ubuntu (dual boot with win for the time being :))on my laptop
**LG S1 express dual**
Unfortunately i noticed that i couldn't hear any sound coming from it. I consider myself a search addict (before you think this is another sound problem etc etc) but i couldn't find a working solution. So i decided to ask for your precious help.

About the problem now:

The laptop's speakers do not make any sound at all.
Headphones work fine.
And the most odd thing of all.
If i leave my pc turned off for some time, about 2-3 hour lets say, when i open it sound is working fine. After 2-3 min though the speakers make some noise and sound disappears (from speakers only that is).
My sound card is a 
**realtek hd ich7 alc883**.
Sound in Windows is working properly.

I have to notice hear that i have tried others distros too with the same problem.

I can provide whatever info you need from the laptop to help you understand the problem, just guide me.

Thanks in advance

---

### Post by 73ckn797 on 2009-02-14
As a first step, I will assume that you have adjusted sound volumes up via right click on the speaker icon at top right and "Open Volume Control" to setup all available input and outputs.

---

### Post by Katmai on 2009-02-14
You assume correctly dear friend.

---

### Post by 73ckn797 on 2009-02-14
OK, Sometimes you have to start at the beginning.

---

### Post by linux_tech on 2009-02-14
what is output of 

```
aplay -l

cat /proc/asound/card0/codec#* | grep Codec 
```

---

### Post by Katmai on 2009-02-14
**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**cat /proc/asound/card0/codec#* | grep Codec**
Codec: Realtek ALC883
Codec: LSI Si3054

---

### Post by Katmai on 2009-02-14
I suspect that the problem is somewhere between these two entries. Kind of loading wrong codec or something? Any ideas?

---

### Post by Katmai on 2009-02-15
I want to add that the sound that the laptop produces sounds like there is an open mic or something that interferes. Still waiting for a guidance mates...

---

### Post by Katmai on 2009-02-15
I could realy use some help here if anybody could spare some knowledge... :)

---

### Post by Katmai on 2009-02-16
Still waiting for a drop of help... I cant stand messing around with hda-intel-******** anymore!!! :)

---

### Post by thefish123 on 2009-09-07
I have the *exact* same notebook and the *exact* same problem.  I have been searching for a solution high and low for well over a year now.

Sometimes, after the computer has been off for a while I get sound from the speakers for a few minutes before it fades out.  Then nothing...

Sound works fine from the headphones all the time 100% consistently.

The Fish

---

### Post by lfaraone on 2009-11-15
Your problem seems similar to mine, which is documented in [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/279478](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/279478) 

See if the attached fix works for you.

---

