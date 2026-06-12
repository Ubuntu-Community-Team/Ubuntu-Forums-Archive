---
title: "gnome-power-manager powersaving behaviour"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by WARvault on 2010-08-16
Hi guys,
I am using gnome-power-manager on a slimmed-down PPC Ubuntu install. I can't seem to configure it to do the very simple, power saving behaviour I want. I feel as if I am using the wrong tool for the job. All I want is to have the display turn off after 20 seconds of inactivity. The CRT in this old iMac must draw dozens of watts and I want to minimize how long it is on for. My system is a G3 iMac, ubuntu-alternate install, Openbox + tint2

WARvault

---

### Post by rburkartjo on 2010-08-16
war have you tried to go to system/preferences/power management and adjust the settings

---

### Post by WARvault on 2010-08-17
I have had a look at the gnome-power-preferences and the gnome-screensaver-preferences dialogues. I think the gnome-screensaver-preferences settings affect when the computer becomes "idle". After being idle, for 10 minutes or more, gnome-power-manager then turns off the display. So not exactly what I am after... Thanks for the reply though!

---

### Post by WARvault on 2010-08-18
I have happily marked this thread closed! I busted out gconf-editor, did a search for "pow" and just changed anything that sounded relevent. 
/apps/gnome-power-manager/timeout/sleep_display (seconds) is the setting I think

I'll do a quick reboot and let you all know if it worked.

***EDIT***
This DID NOT work. It seems when I play with some settings, the daemon works maybe? Any suggestions appreciated...

***EDIT***
I am now trying to add sleep 5 && before gnome-power-manager, whn gnome-power-manager works, I now get almost the behaviour I am after. Still takes 1 minutes to sleep the display, but closer than I was...

---

### Post by WARvault on 2010-08-22
Marking this thread as solved now!
I felt I was using the wrong tool for this job, and now I know.

Added to autostart.sh...

xset +dpms &
xset dpms 0 0 12 &

Now I get 12 seconds before the CRT turns off. Perfect!
Thanks to K.Mandla and [https://bbs.archlinux.org/viewtopic.php?id=94673](https://bbs.archlinux.org/viewtopic.php?id=94673) and man xset

---

