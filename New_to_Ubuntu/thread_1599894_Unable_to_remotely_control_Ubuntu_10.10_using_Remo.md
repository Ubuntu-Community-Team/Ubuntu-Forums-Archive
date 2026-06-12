---
title: "Unable to remotely control Ubuntu 10.10 using Remote Desktop"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by okorkie on 2010-10-18
Hello,

I seem to have a problem relating to Remote Desktop on my newly installed Ubuntu 10.10 PC.  I have gone in and configured Remote Desktop via GUI on Ubuntu 10.10 (System - Preferences - Remote Desktop).  I have enabled it (Allow other users to view your desktop), and have checked 'Allow other users to control your desktop'.  I have also required the user to enter a password, but left 'ask you for confirmation' unchecked.

The problem is this, when I connect within my home network from my XP PC using UltraVNC, it connects just fine, BUT I am unable to remotely control the desktop.  Also, what is unusual, is when I move the mouse around on the Ubuntu PC, I DO NOT see the mouse move around on my Windows session.

Any idea of what is going on??

Thanks in advance!!

---

### Post by rogueleader12345 on 2010-10-18
Do you have port forwarding on your router enabled? I had to set that up before I could get mine to work.

---

### Post by Joshwaa on 2010-10-18
Try [Teamviewer]("http://www.teamviewer.com/index.aspx"), it's great! Lots of features, and very easy to use.

---

### Post by CharlesA on 2010-10-18
Turn off desktop effects.

System >  Preferences > Appearance > Visual Effects

---

### Post by okorkie on 2010-10-18
That worked!!  Thanks so much.

Just a follow up question from this....Does turning off Desktop effects, affect the display output from my graphics card?  I output the VGA output into my VGA enabled Sony Vaio TV, and watch video, e.g. avi, mpg's, and flash video.

---

### Post by CharlesA on 2010-10-18
No it doesn't affect anything. The desktop effects are just more fancy animations.

---

### Post by Old *ix Geek on 2010-10-19
> **CharlesA said:**
> Turn off desktop effects.Thank you! I'd been banging my head against the wall for a while--and that HURTS when you've had a craniotomy! :eek:--trying to figure out why remote connections no longer worked correctly. After upgrading to 9.10 each computer could connect to the others [all Linux], but they couldn't DO anything. Some even had just blank, black screens. Yet if I watched the remote screen in person, the cursor WAS moving--but that didn't do me any good unless I wanted to use the local and remote computers in the same room...which kind of defeats the purpose.

Turning off desktop effects on both computers solved the problem. :)

---

