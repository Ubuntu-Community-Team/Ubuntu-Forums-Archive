---
title: "Camera Woes After Upgrade"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by playing_with_matches on 2009-11-04
Hello,

I upgraded to 9.10 the other day, sweet.  However, now when I connect my Canon Rebel (EOS 350d) to my computer, Ubuntu recognizes it, but Digikam can't grab the pictures from it. Not so sweet.

In the past, I had to unmount the camera in order for digikam to work correctly, but now even unmounting doesn't solve anything.  Any suggestions???

---

### Post by The Cog on 2009-11-04
There was a problem with Jaunty not being able to open cameras properly that could be overcome by killing a process with this command:
> sudo killall gvfs-gphoto2-volume-monitor

I have no idea if that is your problem, or even if it is a problem at all in Karmic. But it's worth a try.

---

### Post by grizato on 2009-11-04
Have you tried another program(cheese, camorama...) so as to get better info on the problem?

---

