---
title: "Problems with Ubuntu"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by shoaibsal on 2009-02-10
Deal All, 

I hope that you all will help me for the following problems.i have

1).Sony Vaio FZ18M Laptop
2) Installed Ubuntu 8.04 Hardy heron.

Following problems have been encountered.

1) When i plug in Headphones, there is still sound in the laptop speakers and not in the headphone.

2) When i suspend/or turn laptop in sleep mode,it never gets back to active mode when i press any key. So i have to shut it down completely and have to restart it again.

Further 
I have tried to solve the sound problem by clicking on the vol control. Normally what i see in Playback Tag are master and PCM Bars only.So there is no question of check or uncheck any option.

Finally here is the detail of my sound card :
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
I hope someone in this forum will help me.Looking forward for replies and solutions.

Regards
shoaib.:confused:

---

### Post by jbrown96 on 2009-02-10
Suspend is usually a Graphics issue. To help with that I need to know about your video card. Post the output of ```
lspci | grep VGA
```

For audio, you may want to try a different audio system. Go to System--->Preferences--->Sound. Try changing all the devices to either ALSA or Pulseaudio. It may be a good idea to restart once you change them to be sure that the system changes. then, test your headphones again

---

### Post by SteveNorman on 2009-02-10
you may want to read through this:



[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

it helped me out

---

### Post by shoaibsal on 2009-02-11
> **jbrown96 said:**
> Suspend is usually a Graphics issue. To help with that I need to know about your video card. Post the output of ```
lspci | grep VGA
```

For audio, you may want to try a different audio system. Go to System--->Preferences--->Sound. Try changing all the devices to either ALSA or Pulseaudio. It may be a good idea to restart once you change them to be sure that the system changes. then, test your headphones again
this is the output

01:00.0 VGA compatible controller: nVidia Corporation G86M [GeForce 8400M GT] (rev a1)

---

### Post by jbrown96 on 2009-02-11
I've had success in the past with the following instructions for suspend

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

---

