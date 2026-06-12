---
title: "Hardware conflict?"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by mike&lt;linux on 2009-11-26
ive installed ubuntu 9.10 and i cant use it because the mouse pointer freezes , the keyboard still works. even if i unplug the usb mouse and plug it back in it doesnt work.i reboot the system and it will work for a bit then do the same thing. i have tried several mice and have the same result. i was wonder if there is some kind of device conflict or hardware config. that are causeing this? if anyone can comment on this issue i would be grateful.

---

### Post by Daveth on 2009-11-26
I never did fix mine, but it did go away when I upgraded my motherboard. Not that is of any use to you, of course! At the time (in August) there seemed to be a lot of it about in various Linux distributions, so i wondered if it was a kernel thing, but clearly not/ less likely if it is still alive. I share your pain over the annoyance this causes.
David

---

### Post by mike&lt;linux on 2009-11-27
thx for the reply. yeah its really annoying that i cant get ubuntu to work. i guess ill just have to stick with xp (sigh) until i can buy a new comp.

---

### Post by ukripper on 2009-11-27
post the output of the following after the mouse freezes again:
```
tail -n 100 /var/log/messages
```

---

