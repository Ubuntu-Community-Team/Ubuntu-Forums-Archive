---
title: "Epiphany Browser starts every time I log in"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by dsantesteban on 2010-11-20
I had an issue where my computer crashed so I had to shut it down, and since then, Epiphany has opened up every time I start up the computer. Any suggestions?

---

### Post by JDShu on 2010-11-20
Maybe it got onto the startup applications list somehow?

Assuming you're on Ubuntu:

Go to System->Preferences->Startup Applications.

In the list, see if Epiphany is there. If it is, then remove it.

---

### Post by acrazyplayer on 2010-11-20
Have you tried looking in the "system" --> "prefrences" --> "startup items" and seeing if it is in there? if so just uncheck it. If not then try completly removing it from your system via synaptic and reboot to see if something still comes up like "could not load ephinay". if not then reinstall it and see if it continues. All of your bookmarks and settings will still be saved if you remove it so you dont need to worry but just incase try making a backup, good luck

---

### Post by ajgreeny on 2010-11-20
You can also make sure nothing is running that you don't want, go to the options tab of Startup Applications, and click the "Remember currently running applications" box.  Now logout and then login again.  Epiphany should not start this time.

---

