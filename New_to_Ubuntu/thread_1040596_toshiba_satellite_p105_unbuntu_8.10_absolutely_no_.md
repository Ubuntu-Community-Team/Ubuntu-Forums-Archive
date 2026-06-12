---
title: "toshiba satellite p105/ unbuntu 8.10/ absolutely no sound?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by hollipharm on 2009-01-15
if anyone can help me get sound that would be great...

---

### Post by Sealbhach on 2009-01-15
Try this. Open up a terminal and type

```
gksudo gedit /etc/modprobe.d/alsa-base
```

Right at the very end of this file, add the follwing line

```
options snd-hda-intel model=laptop
```

Be careful not to change anything else in that file. You will need to reboot for the changes to take effect.


.

---

### Post by hollipharm on 2009-01-15
made the chane and getting ready to reboot.  just wanted to post incase something crazy happens and i cant get back for a while.  also made changes previousely to system>preferences>sound  set all to pulse audio except the mixer and i tried to set it to my sound card?  by the way not for sure how to find out what my sound card is.

---

### Post by Sealbhach on 2009-01-15
> **hollipharm said:**
>   by the way not for sure how to find out what my sound card is.

Type 

```
aplay -l
```

and paste the output here. I'm assuming it's a hda-intel.

Everything you need to try for your sound is here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


.

---

### Post by hollipharm on 2009-01-15
her are the results and i've been to the link you posted multiple times with no luck.  it is possible that my lack of experience with ubuntu that is the problem... lol

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by hollipharm on 2009-01-15
one thing that seems to be odd is that intrepid from what i read functions with pulse audio not oss and it seems that when i look in the applications>sound and video>gnome alsa mixer it has the sound card name conexant cx20551 (waikiki) which in the system>preferences>sound>default mixer tracks is listed as conexant cx20551 (waikiki)(oss mixer)?  looks like if everything needs to be pulse audio this could be a problem?  i have it set to hda intel at this point with no audio working however, i have tried almost every combination possible within these audio settings.

---

### Post by Sealbhach on 2009-01-16
Hi, sorry it didn't work. The only other thing I could suggest is to go through the Sound Problems Solutions guide linked above.


.

---

