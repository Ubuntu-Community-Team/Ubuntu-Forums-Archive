---
title: "compiz/graphics problems"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by 10up on 2009-09-26
Okay, I've somehow managed to royally mess up my settings.

I had everything working fine but something I've done has made it so now every time I boot I get.

"Compiz screen is not composited" error

None of my screenlets or awn starts. I can't min/max windows.  running slowly.

I tried reinstalling xserver-xorg-video-intel and libgl1-mesa-glx but the problem persists.


I'm sure it's probably an easy fix, but I'm horrible at figuring this stuff out

---

### Post by 10up on 2009-09-26
if more information would be helpful I can post it.

---

### Post by pedro3005 on 2009-09-26
Try reinstalling "libgl1-mesa-dri" and reboot.

---

### Post by 10up on 2009-09-26
still nothing.

same error

Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager

---

### Post by 10up on 2009-09-26
any other idea's?

---

### Post by inobe on 2009-09-26
what are some of the stuff you installed,did you follow any guides, maybe you can reverse what was broken.

---

### Post by 10up on 2009-09-26
I was (improperly) trying to get rid of an AWN error.

I removed and reinstalled "libgl1-mesa-glx"
then just installed "libgl1-mesa-dri" due to it not being installed initially.

restarted x "sudo /etc/init.d/gdm restart"

and the system hung.  So I went to a different xserver and did a reboot from the terminal.  Thats when the error started to appear.

I've removed and reinstalled "compiz-wrapper" and the above listed mesa packages with no result.

---

