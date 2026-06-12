---
title: "can't enter wifi security password, locked, red highlight"
date: 2020-08-14
forum: Networking &amp; Wireless
---

### Post by roky1141 on 2020-08-14
i've spent all day on the net looking for someone who's experienced this, but for the first time in about 10 yrs, no one -- went from 16.04 to 18.04, now when prompted to enter my router password, the box is locked, red highlighted -- i'm ok on ethernet, and the system detects my routers wifi signal, but i can't enter the password -- also, on the general tab, i can't activate "all users may connect to this network" because the "save" button is not functional.:confused:

---

### Post by roky1141 on 2020-08-14
fixed! -- this was a fresh install, cause the upgrade messed up a lot of stuff -- the solution to no wifi was to re-install, and this time during the install, not enable automatic login -- i had tried to disable it before the re-install, by editing the folder [COLOR=#666666][FONT=Lato]custom.conf, but it had no effect -- easily might have done something wrong -- but since i had not yet restored my home folder, re-install was easy[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-08-14
FYI automatic login is really really NOT recommended.
Even the current Windows version doesn't allow it by default and makes it harder than ever to explicitly enable it. Surely there's a reason. Please learn good practices. Enjoy.

---

