---
title: "how to uninstall LXDE"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by oziwombat on 2009-09-12
Hi Guy's  , I stuffed up again & installed LXDE .Lightweight Desktop Envrio & now nothing seems to work IE Floppy ,slave H/Drive ,Internet .:confused::confused:
How do I uninstall this & get back to my normal 9.04 Ubuuntu ?
Do I go into Syn package Mgr & uncheck all LXDE & reboot ? 
Cheers Ozi

---

### Post by MelDJ on 2009-09-12
yes. or sudo apt-get remove

---

### Post by mikewhatever on 2009-09-12
Have you installed LXDE on top of Ubuntu/Gnome? If that's the case, just select Gnome under Options at the login screen.

---

### Post by oziwombat on 2009-09-12
> **mikewhatever said:**
> Have you installed LXDE on top of Ubuntu/Gnome? If that's the case, just select Gnome under Options at the login screen.

Thanks Guy's all fixed & Mike ,yes I did install over Gnome .And in future if it ain't broke I wont try to fix it :P:P
This is the best support forum & many thanks for the help .
Cheers Ozi

---

### Post by clicker4721 on 2010-01-31
Well, yes, it worked for me--except for a few things.  Under "Accessories," I still have "LXTerminal;" under "Other" (which I didn't even have before), I have Openbox Session; under "System Tools," I still have "XScreensaver Setup;" and under "System Setting" => "Appearance," I still have two clickables for "Screensaver." Can these be removed through Synaptic Package Manager? If not, how else, or is there a more suggested way?

---

### Post by Liakopaido on 2010-03-20
Try 
sudo apt-get autoremove

---

### Post by happysadhu on 2010-04-08
Hi,
I two have xfce programs still left in my ubuntu desktop even though I've uninstalled Lubuntu/XFCE. *C*[I]licker4721, did you ever find an easy way to uninstall the left over programs?

Sam
[/I]

---

### Post by jheaton5 on 2010-05-17
I installed gdm and gnome.  Then I removed lxde and open box ```
# aptitude remove lxde openbox
```
Now openbox tries to start then aborts and shuts down X which immediately restarts and then tries to start openbox all over again.
How do I set gdm as defalt?
Will this work?
```
# aptitude purge gdm gnome
# aptitude purge openbox lxde
# aptitude install gdm gnome
# dpkg --configure X
```

---

