---
title: "Amarok and Totem Movie Player: can't get sound from both at the same time"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-12-22
Hi Ubuntu Community:

Occasionally I have Amarok and Totem Movie player running at the same time... [COLOR="Red"]**but I can't get any sound when they are both running.**[/COLOR]

:guitar:

In fact when I have both of them running I get no sound at all...  and have to reboot!!]

](*,)


I get sound just fine when only one of them is running, ie only Amarok or Totem Movie Player... but not both at the same time.

How do I fix this?

Thanks!
Phil Smith
Duluthistan, GA

---

### Post by NightwishFan on 2010-12-22
I would say you have to set up phonon to use pulseaudio or something. I have no idea how to do that unless you have the KDE System Settings control centre installed.

---

### Post by nerdy_kid on 2010-12-22
can you use other sound apps at the same time?  say, rhythmbox and totem?  



do this to get kde apps to use ubuntu's default sound system:
```

sudo apt-get install systemsettings

```
then fish for it in your menu (should be either preferences or administration) open it up and hit multimedia then hit phonon and bring the "pulseaudio" entry all the way to the top of the priority list, and then hit "apply device list to" select everything and press OK, then press apply.  restart your computer or logout/in. it should work now.

---

### Post by Old Jimma on 2010-12-24
Hi nerdy_kid;

When I hit: System > preferences > sound, there are no "multimedia" tabs, nor is there anything that refers to "multimedia" under the sound effects, hardware, input, output, or applications tab.

:-s

Phil

---

### Post by nerdy_kid on 2010-12-25
> **Phil Smith said:**
> Hi nerdy_kid;

When I hit: System > preferences > sound, there are no "multimedia" tabs, nor is there anything that refers to "multimedia" under the sound effects, hardware, input, output, or applications tab.

:-s

Phil

sorry, you aren't looking for the "sound" entry, you are looking for "system settings".

---

