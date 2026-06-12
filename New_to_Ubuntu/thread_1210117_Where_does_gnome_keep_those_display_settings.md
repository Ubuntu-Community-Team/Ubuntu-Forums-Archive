---
title: "Where does gnome keep those display settings?"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by moody_mark on 2009-07-11
I upgraded a laptop from 8.04 to 8.10 everything went ok. The laptop usually runs with an external screen as its own screen is broken. After I restarted into 8.10 I changed the display settings in gnome using preferences --> screen resolution. I set the external display to a resolution I wanted and then turned off the laptop display (select the display resolution dropdown and select "off"). The next thing that happened had me kicking myself.

The external screen went black and said "signal out of range". Ok so it didnt like the input, fine. So now I have no screen. The problem is when gnome starts I get the login screen ok it displays fine its just when you login and load your settings in gnome.

So heres my question: Even though my X display is ok and everything works ok, when you login to gnome, some settings must get handed from gnone to X to adjust the display. Where are these settings? I need to get into a command session (CTRL+ALT+F1) and change them.

---

### Post by CatKiller on 2009-07-11
Per-user resolution settings are kept in ~/.config/monitors.xml.

---

### Post by moody_mark on 2009-07-11
> **CatKiller said:**
> Per-user resolution settings are kept in ~/.config/monitors.xml.

:popcorn:

Perfect - thank you so much, a simple thing but well worth knowing

---

### Post by CatKiller on 2009-07-11
It's surprising what turns out to be useful when you're just poking around.

---

### Post by moody_mark on 2009-07-11
We used to be able to mark these threads as "SOLVED" so other people searching can see in a quick search. Also give "thanks" to people... what happened to that?

---

### Post by CatKiller on 2009-07-11
There was some kind of huge database load and in the process of fixing it the Thanks and Solved tools were removed. There's a Sticky about it somewhere.

---

