---
title: "gnome-power-manager window is not visible"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by pradeepkaruturi on 2009-08-22
when i start gnome-power-manager , i can see the thread in the gnome-system-monitor sleeping, i dont see any window of gnome-power-manager
This is also happening with other applications

---

### Post by kaitwospirit on 2009-08-23
Some of these applications might be opening in your tray by default. I think that gnome-power-manager is one of these. When you open gnome-power-manager, does an icon appear in the top right-hand part of the screen?

---

### Post by pradeepkaruturi on 2009-08-24
there is no icon in the tray either.. also my sound does not work sometimes
I have to logout and then login to get the sound working...

---

### Post by Codix121 on 2009-08-24
It's probably not your sound that's broken,
Your probably having an issue with "one-way channeling"
in other words, only one program can use "sound" at a time,
instead of "logging out", just close any program you have open (that is using sound, yes IM messengers, all that use sounds) and then reopen something else, if the sound works then it's "one-way channeling"

best way to fix this is uninstall Pulseaudio and Esound.
(Open synaptic and search Pulseaudio - Click Select For Complete Removal)
then (Search Esound - Click select for Complete Removal)

that's what fixed my sound,
no clue about your other issue.

---

### Post by argos3016 on 2009-08-24
Try adding battery monitor on panel

---

### Post by argos3016 on 2009-08-24
It problaby appear, if don't:
Go System>Preferences>Power blalbla...
General
Yes?

---

