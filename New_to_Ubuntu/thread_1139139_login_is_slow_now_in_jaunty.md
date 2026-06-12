---
title: "login is slow now in jaunty"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Kedster on 2009-04-26
I was wondering if it was just me or ir it's actually something that is true. So i know that "Boot" performance has bean upgraded(lots) but i find my self thinking that the login now takes a lot longer. like i have ti set to login automatically (since Dapper) and on this release it seems quit abit longer, like i have one start up app but that starts up after the time im talking about. I am talking about the time between the Usplash and the desktop.

---

### Post by lovinglinux on 2009-04-26
It seems longer for me too, so I removed some stuff from my session (fusion-icon, --emerald-replace, cairo-dock, screenlets, guake, easystroke and tomboy) and created a script to launch them once the desktop is ready. If I leave them on the session it takes a lot longer to get to the desktop, but clicking the script launcher after the desktop is ready make them load pretty fast.

---

### Post by Kedster on 2009-04-27
hmmm maybe ill have to do that, but the only effects i have running is fusion ( no icon no emerald no dock) and thats it. then i have amsn start up but it starts up after the desktop is running already.

did they remove alot of stuff from the boot time and just put it in the log in time.

altho i have 2 comps that are exactly the same one with intrepid and one with jaunty and jaunty is still usable 15 secs faster so i guess i cant complain

---

### Post by skymera on 2009-04-27
> **lovinglinux said:**
> It seems longer for me too, so I removed some stuff from my session (fusion-icon, --emerald-replace, cairo-dock, screenlets, guake, easystroke and tomboy) and created a script to launch them once the desktop is ready. If I leave them on the session it takes a lot longer to get to the desktop, but clicking the script launcher after the desktop is ready make them load pretty fast.

The only things loading on my session is Compiz, Power manager and update thing.

This still takes a pretty long time.
I made a thread few minutes ago asking if it's possible to cache login whilst at GDM. By the time you've entered your username and password the desktop should be ready :)

Found this yesterday:
[https://wiki.ubuntu.com/DesktopTeam/Specs/Prefetch](https://wiki.ubuntu.com/DesktopTeam/Specs/Prefetch)

---

### Post by lovinglinux on 2009-04-27
> **skymera said:**
> I made a thread few minutes ago asking if it's possible to cache login whilst at GDM. By the time you've entered your username and password the desktop should be ready :)

I don't know, but I have noticed that when the login form shows up, there are still a lot of activity going on, because my fan keeps increasing speed. So I guess they boosted the booting time a little bit by pushing some stuff to load after the login screen is displayed, while the user is still typing the login name and password.

---

