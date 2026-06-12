---
title: "M3N78-VM No audio"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by servicetech on 2009-07-10
Just installed Ubuntu on my M3N78-VM and can everything works great except no sound. Where do I find the "device manager" to start troubleshooting the problem?

I get no sound when run from the Live CD also.

ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by superprash2003 on 2009-07-10
go to system->pref->sound and under sound PLayback try various options given

---

### Post by servicetech on 2009-07-10
It actually works when ran off the Live CD but not the hard drive. I recently replaced the motherboard, it looks like maybe time to back up the home folder and reformat.

---

### Post by servicetech on 2009-07-10
Doing a clean install resolved the sound problem.

---

### Post by servicetech on 2009-07-11
Well it kinda solved the problem, I can get sound when testing through the preferences menu but nothing on DVD, Videos, Firefox, etc.

---

### Post by shifty_powers on 2009-07-11
have you tried alsamixer? (can be accessed by typing that into the terminal)

---

### Post by servicetech on 2009-07-11
Perfect fix :)
Master Volume was set as zero for some reason...

In regards to terminal it seems like the "DOS on steroids".
Apparently Ubuntu isn't quite 100% GUI just yet but terminal does work well if you know all the commands to enter.

---

### Post by shifty_powers on 2009-07-11
yeah i've had that before, the first things i always check with sound issues :D

well as for gui, it is for the most part. you could have done that in gui, i just prefer the terminal for some things :D

some site you might find handy,

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

[http://tombuntu.com/](http://tombuntu.com/)

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

and of course

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

and

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by servicetech on 2009-07-11
I can't find Alsa mixer in the GUI. Without knowing the terminal command there's no way to get to alsa mixer.

I will say terminal is great from the prospective of 'cut/paste' from the forum to get ubuntu to do what you need it to do. Output diagnostic screens are handy also.

---

### Post by shifty_powers on 2009-07-11
heh you won't find alsamixer in there, but you will find a gui to changes the sound 
levels...

---

### Post by fland on 2009-07-28
I have the same motherboard. After installing this motherboard on already installed ubuntu 9.04 i heard no sound. And that problem solved with alsamixer. But here a new problem. I have the keyboard Logitech with multimedia keys, but i cann't change volume with multimedia keys. And what is the funnest thing - system messages with changing volume (standart new 9.04 system messages) appears and showing that volume is changing. And also on old motherboard (with which ubuntu was installed) that keys worked properly. Any suggestions?

---

