---
title: "[SOLVED] problem with screen resolution"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by ET! on 2008-12-25
i unwittingly changed the screen resolution to an incompatible type...the entire screen blacked out...how do i change it back???:confused:

---

### Post by |2A|N on 2008-12-25
Restart your pc and chose the safe boot kernel, then choose the fix X option at the bottom. This happen to me as well. I'm still new to linux so if I'm wrong forgive me.

---

### Post by namdung on 2008-12-25
Reboot in Recovery mode and fix Xorg server.

---

### Post by |2A|N on 2008-12-25
> **namdung said:**
> Reboot in Recovery mode and fix Xorg server.

Ah, thats what I meant to say. :KS

---

### Post by ET! on 2008-12-25
tried that already...didnt work

---

### Post by pyromanic123boom on 2008-12-25
This is easy, you just need to be exact in your typing because you can't see.

1) Log in the user with the problem, wait a good minute for everything to load

2) hit ALT+F2, and wait a few seconds. then type in 'gnome-terminal' with no quotes.

3) wait another few seconds, then type in:

xrandr -s 1

You can change 1 to any size 1-12. 
As long as a screen appears, you can go into System-->Preferences-->Screen Resolution and set it right.

---

### Post by ET! on 2008-12-25
whew...got it back....typing this from ubuntu....thanks buddy

---

