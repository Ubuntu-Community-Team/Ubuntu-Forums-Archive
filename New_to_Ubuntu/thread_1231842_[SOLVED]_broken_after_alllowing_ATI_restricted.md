---
title: "[SOLVED] broken after alllowing ATI restricted"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by jdrodrig on 2009-08-05
Noob question.

I finally succeeded installing ubuntu 9.04 64 on a XPS 435 ATI 4670 HD, but I did the "mistake" of listening to the option of "allowing restricted drivers" for this ATI card (icon that appears on the right upper corner)...and now, my display is broken.

is there a way to "undo" this? Before doing this, I could log in perfectly now I dont get to see the username graphical prompt.

I tried to start on recovery mode and select, "fix graphic problems" with no luck....

I would be willing to re-install again (my installation had a 10minutes life when that happened)...would a new installation replace previos one?

Thanks

---

### Post by lems on 2009-08-05
not sure how to fix it, but when this happened to me i just reinstalled and everything was back to normal. I'm a linux noobie too.

---

### Post by jdrodrig on 2009-08-05
so, new installation will take over, previous ubuntu partitions?

---

### Post by stomper4x4 on 2009-08-05
I had the same problem, and rather than a fresh install, here is what I did. I'm a noob too, so this was pretty easy.

Boot into safe mode during bootup, press esc when it tells you you can

Get to the command prompt.

type:

sudo apt-get remove xorg-drivers-fglrx

then

sudo apt-get install xserver-xorg-video-radeonhd

reboot

Hope this helps.

---

### Post by jdrodrig on 2009-08-05
thanks stomper4x4! you saved my night! Now I can go to sleep knowing I finally installed a workable copy of ubuntu!

---

