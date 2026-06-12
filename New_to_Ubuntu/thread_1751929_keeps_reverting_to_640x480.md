---
title: "keeps reverting to 640x480?"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by jimstolz76 on 2011-05-07
I've got a headless 10.10 box in a closet... I mainly use it as a NAS, but occasionally need to get to the GUI.  I've got a monitor connected to it, but is turned off 99.9% of the time.

Every few months I log in and it's stuck at 640x480.  I can only assume this happens after an update.  Unfortunately I don't use the GUI enough to notice the timing... 

I've fixed this before by mucking around in xorg.conf.  This time it's not fixing it.  This time I've even wiped out everything so it's just a blank file (still have xorg.conf.backup) and it's still booting to 640x480.

The default size for this monitor is 1152x864, and I use TightVNC to reach the GUI remotely.  (The local monitor also displays 640x480.)  Can anyone point me in the right direction?  The freakin' GUI is so small I can't even work with the windows on the screen. LOL

---

### Post by powerpleb on 2011-05-07
What's your graphics card? Have you noticed whether it happens after kernel updates?

---

### Post by jimstolz76 on 2011-05-07
It's an Nvidia GeForce 5200, which I now remember reading about a bunch of problems with...

Yes, I think it's after kernel updates.  Something I just did got it back to 1024x768 which is acceptable, but it's probably just another update away from breaking.

---

### Post by colin.p on 2011-05-07
I have the same card in an old Athlon 1800+, that's my download server. About a month or so ago, I got the same problem, on boot-up, with my screen being 640X480, until I did a re-boot. Then all would be good until the next boot-up. As it was always on, the only time I re-booted was after a kernel update,  but then I would re-boot again and the screen would be back to 1024x768, where it's supposed to be.
I fixed it "permanently" (if such a thing is possible) when I updated the NVidia driver to the "current recommended" and now after a couple kernel updates, all is well with the world again and the display stays at 1024x768.

---

