---
title: "Control Alt Delete (or System's monitor) Doesn't work"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by icyest on 2008-12-16
It says only one process is running. This cant possibly be. There are clearly three windows open as you can see at the bottom.
[IMG]http://img101.imageshack.us/img101/3329/screenshotrk3.png[/IMG]

I was told that this was suppose to be the Linux's CTRL ALT DEL?

---

### Post by damis648 on 2008-12-16
That is odd... do you get the same result from running
```
top
```
in terminal?

---

### Post by OutOfReach on 2008-12-16
Really odd.
Try clicking on the View menu and selecting 'All processes' (or something along the lines of that, I don't use GNOME).

---

### Post by icyest on 2008-12-17
Do you happen to know how to assign CTRL ALT DEL to open up system monitor?

---

### Post by bryncoles on 2008-12-17
for icyest:

i know how to assign keys to processes! first, system, preferences, keyboard shortcuts. make sure the keys you want to assign arent already doing something. 

then, press alt-f2 to bring up the run dialogue. type 'gconf-editor' and press return. navigate to apps, metacity, keybindings and fill your boots!

or, if this scares you (it scares me) the easier way is install conpiz-settings manager from synaptic.

system, settings, compiz settings manager. general options, commands, keybondings. there you go! do it the compiz way, its much easier!

---

### Post by Pjotrovitz on 2008-12-17
Are you running the other apps as root? Because the monitor run as your user will not show the apps/processes started with other users.

---

### Post by icyest on 2008-12-17
> **Pjotrovitz said:**
> Are you running the other apps as root? Because the monitor run as your user will not show the apps/processes started with other users.

How would I exactly know if I'm running as root?

---

### Post by lametike on 2008-12-17
either you use sudo or "root@(your computer name):"
at the start of the command.
normally when you open it will be (your username)@(your computer name):
'sudo root" to get the root(or just use sudo as it seems that ubuntu had remove the root account)

---

### Post by bryncoles on 2008-12-17
@ icyest:

you can also open a terminal and type 

```
top
```

this will tell you what processes are running, and whether they're running as your user, or as root!

---

