---
title: "high pitched noise"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by whitethorn on 2010-04-30
Hi,

I have a 
Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

I noticed that whenever the PCM slider is at 100% I get really wierd noise.  I need to keep it at around -3db.  How do I get that to work? I can't even move the slider around anymore.

---

### Post by whitethorn on 2010-05-05
bump

---

### Post by quadproc on 2010-05-05
> **whitethorn said:**
> Hi,

I have a 
Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

I noticed that whenever the PCM slider is at 100% I get really wierd noise.  I need to keep it at around -3db.  How do I get that to work? I can't even move the slider around anymore.
Which software version(s) are you running?

My motherboard also has an ICH10 but I don't have any audio problems running Ubuntu 9.10.  I am waiting until 10.04 gets the majority of its bugs fixed before I try that release.

quaproc

---

### Post by lidex on 2010-05-05
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by whitethorn on 2010-05-08
I did a couple updates and now my ubuntu won't boot properly.  I haven't really had time to try to fix it (I think it was a kernel panic) I was planning on doing a clean install anyway. But I can give you some of the output from the commands from my arch installation (installed it on the weekend, but I do still want to fix the pulseaudio problem).

```

uname -a
Linux wt-arch 2.6.33-ARCH #1 SMP PREEMPT Mon Apr 26 19:31:00 CEST 2010 x86_64 Intel(R) Core(TM)2 Quad CPU Q9650 @ 3.00GHz GenuineIntel GNU/Linux

```
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```

Advanced Linux Sound Architecture Driver Version 1.0.21.

```
```

Codec: Realtek ALC1200

```

I guess the only difference between running these commands in ubuntu to arch would be the kernel version, distro, and maybe the alsa version.

Is it possible to set the maximum value of the pcm slider to be -3dbs less than the actual maximum?

---

### Post by lidex on 2010-05-08
You could try this, but I'm going on limited information here. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel probe_mask=1  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and

---

### Post by 3rdalbum on 2010-05-09
You probably shouldn't have your PCM set to 100%. On most sound cards you'll get distortion. In your case, you're getting high-pitched noise. Keep it at 95% or lower and you should be fine.

---

