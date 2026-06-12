---
title: "Cannot access any programs no side bars"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by DRC001 on 2011-05-12
Total NOB here!!! 
 
I've been using LINUX now for about 6 months and just up graded to 11.04. In my youthful enthusiasm (I'm 54) I have been able to pull off a real *^&#$?. I was in the system settings, changing how I wanted the screen to look and work and some how switched off the side bar with all of the varous ICONS and also the top bar. The computor does bootup asking me for my password and it lets me know that it has established the wireless network etc. But all that appears on the screen is the wallpaper and what folders I had on the desktop. I can make more folders and delete them, but I cannot do anything else. I try putting the cursor on all side of the screen and in the corners and nothing comes up or out. 
 
Does anyone know of a way to fix this?

---

### Post by Hedgehog1 on 2011-05-12
Please do a **<ctrl> + <alt> + t** to get the terminal.

From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```

There will be some error messages - ignore them please.

Logout **<ctrl> + <alt> + <Delete>** and reboot...

***The Hedge***

:KS

---

### Post by beew on 2011-05-12
Looks like you have disabled Unity somehow. Open any folder, on the left panel choose "file sytems", then go to /usr/share/applications and find the ccsm (Compiz Configuration Setting Manager) and click it open, from there find Unity and check the box to re-enable Unity.  You may need to reboot.

I think there should be some mechanism to prevent people from accidentally disabling Unity, it is not just another Compiz plugin since the desktop now depends on it.

---

### Post by DRC001 on 2011-05-12
It's the left hand panel/side bar that I cannot access

---

### Post by DRC001 on 2011-05-12
The Hedgehog RULES! This worked great, Thanks

D Carlson

---

### Post by Hedgehog1 on 2011-05-12
> **DRC001 said:**
> [SIZE="3"]The Hedgehog RULES! This worked great, Thanks[/SIZE]


Ahh yes...

I can take any amount of this... :D

***The Hedge***

:KS

---

