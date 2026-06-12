---
title: "How to make login window shake on bad password?"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-10-22
Hey everyone,

I was using my friend's macbook pro the other day and noticed that when a bad password is entered into the login window, the window "shakes" or "quivers" back and forth. Is there any way to add this visual feature to the Ubuntu login window?

Thanks
:)

---

### Post by elliotn on 2009-10-22
that could b kul

---

### Post by mcduck on 2009-10-22
Doesn't it already do that? At least the gnome-screensaver's lock dialog (the one you see if you lock the screen suspend or hibernate) does that..

---

### Post by asuastrophysics on 2009-10-22
yeah the lock screen window does that, but not the main login window. 

i just found this forum [http://ubuntuforums.org/showthread.php?t=1264840](http://ubuntuforums.org/showthread.php?t=1264840)

that installs a program called apple shake...dunno if the project is related.

---

### Post by asuastrophysics on 2009-10-22
EDIT: No, the link i gave is to a video editing software program, which is still cool...but not what i was looking for.

---

### Post by mcduck on 2009-10-22
Ok, if you are still using 9.04 then you should be able to enable that by adding "Quiver=1" into /etc/gdm/gdm.conf under the "[greeter]"-section.

It doesn't seem to work in 9.10 though, but I know lots of things have changed in GDM in 9.10 (for example there is no gdm.conf) so that might be the reason.. :)

---

### Post by asuastrophysics on 2009-10-22
hmm i tried changing quiver to 1, but i still don't see a shake. maybe this is due to my modified login window? 

:rolleyes:

---

