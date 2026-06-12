---
title: "Audio problems"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by nesdis on 2009-02-03
I recently installed 8.10 on a DELL optiplex 330 desktop machine. However no matter what I do I cant get the sound to work.

Does anybody know what is happening?

Thanks !

---

### Post by abn91c on 2009-02-03
run this ```
aplay -l
```

---

### Post by abn91c on 2009-02-03
use this guide, page one, start at General setup...., stop at Saving sound....
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by phr0ze on 2009-02-03
The latest kernel stopped my sound from working... maybe that happened to you too. When you boot, press escape at grub and choose one kernel before. (not the recovery kernels, just go down two).

See if that helps. It brought my sound back.

---

### Post by nesdis on 2009-02-04
I tried

```
aplay -l
```

and this is the response I got
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Which means the sound card has been detected. I did as the guide says.. I started up the alsa mixer. The mixer was unmuted to begin with. Yet when I try testing the sound (System->Preferences->sound->test) I get no response. There is no physical problem in the audio jack or anything coz it works fine on windows.


The sound has not been working from the start. regardless of the Kernel. I had 7.04 at first. upgraded to 8.10 recently. didn't work on any of those either

---

### Post by Cresho on 2009-02-04
not sure but you may need to use alsamixer in terminal..if it works.

---

### Post by nesdis on 2009-02-06
OK here's the thing. 

The audio WORKS on ubuntu 7.10. (just installed it on a different partition as recommended by to me by a friend) But not on 8.10. It doesn't work on any of the kernel versions of 8.10.... neither -27-9 nor 27-11. 

Also there's a problem with kernel 27-9.. the system doesn't shutdown and i need to cold boot it every time. the problem has been fixed on 27-11. So i'd prefer to use the latest version.

The only thing i don't understand is while the sound fine on a lower version how does it not work on a later version??

---

