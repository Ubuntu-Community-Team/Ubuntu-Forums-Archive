---
title: "loss of task bars in unity"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by djm on 2011-06-04
I have just got used to unity which i think is not too bad when compared with gnome 3. I changed  settings in compiz set up under system settings to try to get the 3d graphics running, which caused the loss of both the top bar and the hidden task bar. if i move the mouse to the top left hand corner of the screen nothing happens and as there is no top bar i cannot close the pc down.
can anyone help me to get theses back short of reinstalling 11.04 which will cause me a lot of work reinstalling software.
yours dave  :P

---

### Post by Laforge129 on 2011-06-04
> **djm said:**
> I have just got used to unity which i think is not too bad when compared with gnome 3. I changed  settings in compiz set up under system settings to try to get the 3d graphics running, which caused the loss of both the top bar and the hidden task bar. if i move the mouse to the top left hand corner of the screen nothing happens and as there is no top bar i cannot close the pc down.
can anyone help me to get theses back short of reinstalling 11.04 which will cause me a lot of work reinstalling software.
yours dave  :P

I've not tried the graphics but that sounds like the KDE4E Bug.   Can you do anything with the toolbar or is it not even there?

[https://bugs.launchpad.net/ubuntu/+source/plasma-widget-networkmanagement/+bug/741200](https://bugs.launchpad.net/ubuntu/+source/plasma-widget-networkmanagement/+bug/741200)

---

### Post by djm on 2011-06-04
no I cant do a thing, the only way i can get on here is that i have a icon for firefox on the desktop. with no top bar the only way I can close down is to hit the power button.
dave

---

### Post by howefield on 2011-06-04
Can you press Alt + F2 keys and try the command

```
unity --reset
```

---

### Post by djm on 2011-06-04
no if i press alt + f2 nothing happens, the only f key that does anything is alt+f4 which closes the current running program. if I click the minimize button fire fox disappears and I have to call it again then go to history to get back here.
dave

---

### Post by wildmanne39 on 2011-06-04
> **djm said:**
> no if i press alt + f2 nothing happens, the only f key that does anything is alt+f4 which closes the current running program. if I click the minimize button fire fox disappears and I have to call it again then go to history to get back here.
dave
Hi, try ctrl+alt+t then run
```
unity --reset
```let it run for about three minutes,it will never say it is done and then reboot  ctrl+alt+del.

---

### Post by djm on 2011-06-06
what i have found is very strange, i booted the laptop up in ubuntu classic and unity started i thought this was very strange so this morning i tried it in ubuntu again and it was still in the failed state, reboot into classic and unity runs......spooky. i will try what you said and come back
dave

---

### Post by djm on 2011-06-06
nothing, it seems that when unity is in failed state the keyboard is not recognized so nothing works, at least i still can use unity even if it is meant to be classic. i have noticed that in the failed state ubuntu crashes back to the sign in screen mostly when changing pages on facebook.
dave

---

