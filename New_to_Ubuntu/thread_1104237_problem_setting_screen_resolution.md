---
title: "problem setting screen resolution"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by mysticaltopher on 2009-03-23
I installed Ubuntu on a room-mates desktop computer and it has a Nvidia TNT2 graphics card....I know, not compatible.  I was wondering if there is a way to boost the resolution beyond the 800x600 to 1024x768?  I looked at his xorg.conf file through gedit, (I'm not sure this is where I would even fix the problem) and it looks like this:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Do I need to delete either the screen or monitor sections or can I add in the new screen resolution to this file?  Please help, I've been trying to fix this problem for 3 weeks now....Thanks!

---

### Post by cariboo on 2009-03-24
You could use the open source nv driver. You could modify the xorg.conf file to look like this:

```
Section "Device"
Identifier "Configured Video Device"
Driver     "nv"
Option     "Nologo"     "True"
EndSection
```

Jim

---

### Post by Bachstelze on 2009-03-24
> **mysticaltopher said:**
> I installed Ubuntu on a room-mates desktop computer and it has a Nvidia TNT2 graphics card....I know, not compatible.

Eh? Of course it is compatible! You should see the nvidia drivers in the Restricted drivers manager.

---

### Post by kevmitch on 2009-03-24
Just to make sure, you have tried going to System->Administration->Hardware Drivers, right? Otherwise, yeah "nv" is the way to go.

---

