---
title: "computer turned off midway through 10.4 update, don't know where to start fixing this"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by rippedelastic on 2010-05-15
I had karmic and, after updating through the update manager, as I usually do, I decided update to lucid. The installation bar got to about 1 hour left to complete installation, and the computer got accidentally turned off. Now when I boot I get a screen saying "ubuntu 10.4" and a loading bar and nothing happens. I decided to Ileave it for about 5 hours and there was no change. 

Now I don't how and where to start fixing this mess. Assuming that it's half installed and not going to sort itself out, I guess I should go back to the "Windows XP Recovery Centre" partition and well...uninstall ubuntu completely, with my karmic and improperly installed lucid, and then reinstall lucid? Could someone tell me how to do that? Also is there any chance that I can save what I had on my karmic partition?

Thanks for any advice you can give me!

---

### Post by theozzlives on 2010-05-15
Try holding down the shift key to get a boot menu. Boot recovery mode, drop to the root prompt and type:
```
dpkg --configure -a
```
I don't know if that'll work, but that's what I would try first.

---

### Post by rippedelastic on 2010-05-15
hey that seems to be working. Well, I selected install the latest update,  in safe mode, through packages and it's been doing an awful lot of "configuring" for the past 10 minutes :) I'll let you know what it does when it finishes this.
Thanks alot!

---

### Post by rippedelastic on 2010-05-15
hey it worked! 
Thank you so much! :)

---

