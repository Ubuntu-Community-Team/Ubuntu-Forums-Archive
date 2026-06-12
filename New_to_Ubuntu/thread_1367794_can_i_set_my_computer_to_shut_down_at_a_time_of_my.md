---
title: "can i set my computer to shut down at a time of my choiseing"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by blake7 on 2009-12-29
yea i like my computer to run all night then turn it self of in the morring
if i can do that how 

cheers

---

### Post by tom.swartz07 on 2009-12-29
> **blake7 said:**
> yea i like my computer to run all night then turn it self of in the morring
if i can do that how 

cheers

Yes sir!

open a terminal and enter

```
sudo shutdown HH:MM
```
HH:MM is time in 24hr format

you could also type ```
man shutdown
```
to read up on other uses
(hit q to exit)

Have Fun!

---

### Post by taurus on 2009-12-29
What you want to do is to add an entry in /etc/crontab to specify what time you want the cron daemon to run the shutdown -h now command to shut down your machine.

---

### Post by gdonwallace on 2009-12-29
You can setup a time that you want your system to shutdown through the crontab.  This is the file that handles automated tasks for Linux.  It can be difficult to edit, so I would suggest opening synaptic package manager and installing the program gnome-schedule.  

Gnome-schedule will create and edit a crontab file through the GUI.  You can also go back and change settings to make it work the way you want.

The one thing that will be a little odd is the command that you want crontab to execute.  

To shutdown the command will be **shutdown now**

If you want to shutdown and restart the command is **shutdown now -r**

Use the help and edits available in the program and it is easy to use.

---

### Post by blake7 on 2009-12-29
cheers
ps what time is it where you are????

---

### Post by gdonwallace on 2009-12-30
I'm in Oklahoma, Central time zone, and it is currently 1230 in the afternoon.

---

