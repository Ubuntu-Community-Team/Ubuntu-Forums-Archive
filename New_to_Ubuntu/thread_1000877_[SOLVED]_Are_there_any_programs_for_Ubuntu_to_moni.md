---
title: "[SOLVED] Are there any programs for Ubuntu to monitor CPU temp?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by gshockxc on 2008-12-03
I was using Motherboard Monitor 5 on my XP system, which will soon become another Ubuntu box.  And I like to keep an eye on the CPU temps.  No issues lately, but I like to monitor it as I load up the CPU.  Is there something like this available for Ubuntu?  

If not, it might be a fun project to make one.

---

### Post by Michael.Godawski on 2008-12-03
Try lm-sensors. It is in the repositories.
[http://www.lm-sensors.org/](http://www.lm-sensors.org/)

---

### Post by oilchangeguy on 2008-12-03
> **gshockxc said:**
> I was using Motherboard Monitor 5 on my XP system, which will soon become another Ubuntu box.  And I like to keep an eye on the CPU temps.  No issues lately, but I like to monitor it as I load up the CPU.  Is there something like this available for Ubuntu?  

If not, it might be a fun project to make one.

there is ( don't remember the name) but look in add/remove, under system. it should be there. also if yours is a newer computer look in the bios for pc health. you should be able to set a shut down temp.

---

### Post by tjwoosta on 2008-12-03
if you want i nice little gnome panel applet that tells you the temp you can use sensors-applet  (its also in the repos)


sensors-applet uses lm-sensors to get the temp and displays it on your gnome panel


after installing lm-sensors and/or sensors-applet you will need to configure the sensors   ( you may need to use sudo for this, i cant rememmber)

```
sensors-detect
``` (after running this command just answer all of the questions)


after configuration, to add the applet to the panel you will need to right click the panel and choose "add to panel" then find the new temp sensor in the list

---

### Post by gshockxc on 2008-12-03
Thanks to all for your help.  This is great info.  It's incredible how easy it is to pick this stuff up once you get started.  Thanks for helping become a "Not-so-Noob!"  ;-)

---

### Post by binbash on 2008-12-03
you may also want to check conky

---

### Post by gshockxc on 2008-12-04
I'm confused.  I found both of these: conky and server-applet in the repos.  I installed them, but they don't show up in my applications menu.  I'm sure they are there somewhere, I'm just not sure how to find them.

---

### Post by iaculallad on 2008-12-04
> **gshockxc said:**
> I'm confused.  I found both of these: conky and server-applet in the repos.  I installed them, but they don't show up in my applications menu.  I'm sure they are there somewhere, I'm just not sure how to find them.

Here, follow this [guide]("http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html") to auto-start your conky application in Ubuntu.

---

### Post by tjwoosta on 2008-12-04
> I'm confused. I found both of these: conky and server-applet in the repos. I installed them, but they don't show up in my applications menu. I'm sure they are there somewhere, I'm just not sure how to find them.

first off its its sensors-applet not server-applet

secondly the sensors applet can be found in the list when you right click you gnome panel and choose "add to panel"  (not in the applications menu)

---

### Post by Yownanymous on 2008-12-04
Also I think enlightenment desktop environment comes with one preinstalled.

---

### Post by gshockxc on 2008-12-04
> **tjwoosta said:**
> first off its its sensors-applet not server-applet

secondly the sensors applet can be found in the list when you right click you gnome panel and choose "add to panel"  (not in the applications menu)

Sorry for the typo.  I did find sensors-applet in the repos, and it grabbed the lm-sensors file too.  

What are you calling the gnome panel?  I'm sure I've seen it, just not knowing what it was called.  Wait, is the "panel" what I might call the toolbar at the top of the screen?

---

### Post by madsc89 on 2008-12-04
> **gshockxc said:**
> Sorry for the typo.  I did find sensors-applet in the repos, and it grabbed the lm-sensors file too.  

What are you calling the gnome panel?  I'm sure I've seen it, just not knowing what it was called.  Wait, is the "panel" what I might call the toolbar at the top of the screen?

Yes. It is where applications, places, system, shutdown button etc. is. Right click on an empty spot an choose add to panel.

---

