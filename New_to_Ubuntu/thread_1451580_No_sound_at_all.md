---
title: "No sound at all"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by CaitlinS on 2010-04-10
Today when I turned my computer on, there was no sound. Neither the speakers nor my headphones work. I've tried playing songs in Rhythmbox and also online. 

The volume has been turned up. I went in to Sound Preferences, and couldn't see anything obviously wrong (though to be honest I'm not really sure what I'm looking for).

In another thread it was suggested to type aplay -1 into terminal, which I did, but I now have no clue what to do with it. This is what I got back:

caitlin@caitlin-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thanks for the advise!! I'm pretty new to this so as specific directions as possible would be fantastic.

Oh, and I have 9.10. When I put in uname -r it gave me 2.6.31-20-generic which I think is my kernal?

---

### Post by CaitlinS on 2010-04-10
It appears to be fixed. I have no idea why though. I don't think I did anything...What do you think it could have been, in case it happens in the future?

---

### Post by NCLI on 2010-04-10
Did you run an update?

---

