---
title: "no sound on toshiba laptop"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by eddski on 2009-04-06
I have a toshiba u205 w/intel sound but I have no sound. Sometimes I get something on bootup, but nothing else. I tried to do a search for audio and looked like many game postings. Anyway I would like to get sound, or get pointed in the right direction..

---

### Post by Peter09 on 2009-04-06
What version of Ubuntu are you running?

---

### Post by eddski on 2009-04-06
I am using Ubuntu 8.10

---

### Post by markbuntu on 2009-04-06
Look in here


[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by Sealbhach on 2009-04-06
This worked on my brother's Toshiba laptop.

Open up a terminal. Type:
```

sudo gedit /etc/modprobe.d/alsa-base
```

This will open up a text file. Go to the very end, and add another line, copy and paste in this:

```
options snd-hda-intel model=toshiba
```

Save the file and close.

Reboot.

---

### Post by eddski on 2009-04-06
I tried Sealbehach's reco and that did not work. Anything else I should try?

---

### Post by lhb1142 on 2009-04-07
> **eddski said:**
> I have a toshiba u205 w/intel sound but I have no sound. Sometimes I get something on bootup, but nothing else. I tried to do a search for audio and looked like many game postings. Anyway I would like to get sound, or get pointed in the right direction..

:KS Have you checked your Volume Control, both the main one as well as the volume control (if any) in the program(s) you are running?

In the main Volume Control (icon located in upper panel at the right side), right-click it but do NOT click on "preferences" Click on "Open Volume Control." At the bottom of the box, you will see another "Preferences" choice. Click on that and proceed accordingly. Make sure every option is checked and examine all of them to make sure the settings are to your liking. Obviously, make sure that no playback device is muted.

Some other programs (VLC for example) have their own volume controls; make sure that these are set to maximum. As a matter of fact, in my opinion, all volume controls within programs should be set to maximum and the overall volume should be set by the master control. It's too easy to set a program's volume to a low level and forget doing that. Then when using the program, the level is too low even when the master volume control is set to 100%.

I hope that this is of some use to you. ):P

---

### Post by eddski on 2009-04-07
I tried markbuntu's suggestion, but it did not work. I have a Toshiba U205 and still have no audio.

---

### Post by eddski on 2009-04-07
below is the output from the command aplay -l...

**** List of PLAYBACK Hardware Devices ****
E: shm.c: shm_open() failed: Read-only file system
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

can anyone tell me anything from this?

---

### Post by Sealbhach on 2009-04-07
> **eddski said:**
> I tried Sealbehach's reco and that did not work. Anything else I should try?
 
Did you reboot, it only works if you reboot?
 
If not try
 
model=laptop
 
 
.

---

### Post by eddski on 2009-04-13
this is my output from aplay -l

**** List of PLAYBACK Hardware Devices ****
E: shm.c: shm_open() failed: Read-only file system
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

can anyone tell me what this means?

---

