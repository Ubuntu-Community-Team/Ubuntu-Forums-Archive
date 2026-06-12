---
title: "Display oversized after enabling nvidia"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by tweety_r78 on 2010-02-05
I finally managed to get the sound working after enabling the nvidia hardware on the computer. But after the reboot, the desktop got too big for the monitor. As a result I couldn't see my menubars anymore. I managed to disable the nvidia, so my desktop is now back to normal, but again with no sound..... :(
I've googled my head off, but haven't found any good solutions yet.
(It's the Ubuntu 9.10 version)
could reeeaallly need some help with this....

---

### Post by audiomick on 2010-02-05
Hi. A bit more info about your hardware might help, like video card model, which driver you have or had installed for it, what sort of monitor and which resolution it should have.

Theoretically, once you have enabled the nVidia **graphics** driver, you should just have to run
```
gksu nvidia-settings
```
to set things up.

---

### Post by Iowan on 2010-02-05
I recently had the opposite problem - there was about 1/2" band around the edge of display. As monitor is used between a couple of computers, I checked and found the full-sized display refresh is 60 Hz, and the undersized on was 85Hz. Dropping to 75 Hz made the display fit. If your Nvidia is capable of faster refresh...

---

