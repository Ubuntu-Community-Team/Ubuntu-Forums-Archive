---
title: "Going to sleep?"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by old_dope on 2009-04-07
It drives me up the wall when for instance i am watching a film on the computer via the Internet and all of a sudden the screen goes black and a screen saver kicks in. Could anyone tell me how to prevent this from happening in future please. Thanks in advance

---

### Post by ubername on 2009-04-07
> **old_dope said:**
> It drives me up the wall when for instance i am watching a film on the computer via the Internet and all of a sudden the screen goes black and a screen saver kicks in. Could anyone tell me how to prevent this from happening in future please. Thanks in advance

Have you tried messing with system>preferences>screensaver ?

---

### Post by sdennie on 2009-04-07
Try this: [ HOWTO: Disable screen saver while Flash is running]("http://ubuntuforums.org/showthread.php?t=1090393")

---

### Post by kerry_s on 2009-04-07
/etc/X11/xorg.conf

```
Section "ServerFlags"
     Option "BlankTime" "0"
     Option "StandbyTime" "0"
     Option "SuspendTime" "0"
     Option "OffTime" "0"
EndSection

```

---

