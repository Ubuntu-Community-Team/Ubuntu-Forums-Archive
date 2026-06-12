---
title: "lost my volume slider from top right panel bar"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by RotorRick on 2011-04-22
10.04LTS, Gnome 2.30.2

The top right panel bar, where the networking, date, chat and shutdown icons are displayed, had a volume icon with a slider. I think I shut it down or deleted it by accident. 

Sounds still work just fine...but I can't adjust the overall system volume as that icon/slider is no longer visible there.

I've been trying for an hour to find a setting to reinstate it, but found nothing. Anyone have suggestions for this?

Thanks!:D

---

### Post by Frogs Hair on 2011-04-22
Right click the top panel select add to panel and from the menu add the indicator applet , which include the mail and sound icon .

---

### Post by Fraoch on 2011-04-22
(already answered)

---

### Post by RotorRick on 2011-04-22
Thanks, that solved the problem!

---

### Post by rogermunns on 2011-04-24
Thanks, this also helped me.

Couldn't the add-on be labelled to show it includes 'sound'? It's certainly not obvious.

---

### Post by dcsoldschool53 on 2011-04-24
> **RotorRick said:**
> 10.04LTS, Gnome 2.30.2

The top right panel bar, where the networking, date, chat and shutdown icons are displayed, had a volume icon with a slider. I think I shut it down or deleted it by accident. 

Sounds still work just fine...but I can't adjust the overall system volume as that icon/slider is no longer visible there.

I've been trying for an hour to find a setting to reinstate it, but found nothing. Anyone have suggestions for this?

Thanks!:D

Also, you can click System > Preferences > Startup Applications. Scroll down and look for Volume Control and put a check mark in the box next to it. If you don't see it there,  click the add button. In the pop up box, type in the name Volume Control. For the command, type in gnome-volume-control-applet. Add an icon and a comment

---

### Post by silbar on 2011-04-24
Related problem: in Ubuntu 10.4, I now and then lose the shutdown icon at the right end of the panel.  To shutdown, then, I have been typing "sudo shutdown now" at a terminal prompt.  This does a shutdown but comes to a point on the screen bearing the message "init: disconnected from system bus".  At which point I can then power down the computer gracefully.

Thanks to Frog's Hair, I can now put the shutdown icon back on the panel and proceed to shutdown normally.

   Rico Silbar

---

### Post by bidax on 2011-07-17
Thanks a lot for the post!

---

