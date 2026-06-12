---
title: "I've jiggered my Kubuntu task manager"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by geoff_p on 2009-12-20
I am a complete novice at Linux-based systems, though I have spent some time with Winslop.  This week I installed Kubuntu, and generally like it, however ....
I have cocked-up the 'task bar' (sorry, I don't know its proper name) 

I used to have the standard "task bar" layout, i.e. Kickoff, Quick Access at left, then window 'names' e.g. Firefox, Dolphin etc, then the System tools at the right-hand-side.

Since I "fiddled about", all I get is (reading from Left to Right):
  Kickoff, Quick-Access ...space... Clock/calender, Indicator Display (always shows 'No Applications Running'), Skype, Sound volume, Klipper, Internet 'indicator?", Amarok, i (Notification and Jobs), USB, Show-the-Desktop, these last group smack in the middle of the task bar.

The effect is that if I minimise a working window, it simply vanishes.  Not so bad for Dolphin, I can simply open a new instance and track through to wherever, but it's disastrous for Firefox because a new instance will simply be a clean slate, with none of my tabs.

But if I restart the system, Firefox will happily bring back the 'lost' instance, as well as the current one.

Please, help me get my task bar back to normal,

Geoff
Thailand

---

### Post by Zorael on 2009-12-21
Right click the panel and pick *Unlock Widgets* (unless it's already unlocked). That should make the cashew appear as that little nut-shaped thing at the bottom right of the panel. Click it and pick *Add Widgets*. Scroll down the menu that pops up, or use the search function to find **Task Manager**. Click *Add Widget* or just drag it to where on the panel you want it to be.

---

### Post by geoff_p on 2009-12-25
Zorael, Many thanks for that; I have 'some' widgets back but only at the expense of destroying the original System Tray.
Still, 'tis better than nothing,
So Thanks again,
Geoff

---

### Post by Zorael on 2009-12-25
You can also wipe your plasma settings to make it restore the defaults, by removing (or renaming) all files beginning with **plasma** in **~/.kde/share/config/**.
```
$ mkdir ~/plasmabackup					# create directory to place backups in
$ mv ~/.kde/share/config/plasma* ~/plasmabackup		# move the configuration files to that directory
$ kquitapp plasma-desktop; sleep 5; plasma-desktop	# terminate and restart plasma
```

---

