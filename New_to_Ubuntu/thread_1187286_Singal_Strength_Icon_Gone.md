---
title: "Singal Strength Icon Gone"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by TopFan on 2009-06-14
I accidentally removed the wifi signal strength icon from my top panel. I can't for the life of me work out how to get it back.

Any help much appreciated!

This is what I'm talking about:

[IMG]http://i684.photobucket.com/albums/vv208/MacTop/ubuntu-wifi-1.jpg[/IMG]

---

### Post by s.fox on 2009-06-14
Hi,

It's called the network manager applet. Open a terminal and make sure it comes back with:  

```

nm-applet 

```

You should also make sure that the applet is enabled in: 

**System -> Preferences -> Sessions -> Startup programs.**

-Ash R

---

### Post by TopFan on 2009-06-14
I don't have a 'Sessions' option under System > Preferences.

What do I do with the code?

---

### Post by drs305 on 2009-06-14
> **TopFan said:**
> I don't have a 'Sessions' option under System > Preferences.

What do I do with the code?

It's now under System, Preferences, StartUp Applications. Just make sure it is enabled.

By the code, do you mean "nm-applet"? Just open a terminal (ALT-F2) and run that command to make sure it is running.

---

### Post by fooman on 2009-06-14
right click on an empty area of the top panel and choose "add to panel" from the drop-down list.

in the list that pops up,  click on "notification area",  then click "add".

see if that gets it back.

---

### Post by TopFan on 2009-06-14
Nice one. Found it.

But what do I do with it? The check box is already checked.

---

### Post by s.fox on 2009-06-14
> **drs305 said:**
> It's now under System, Preferences, StartUp Applications. Just make sure it is enabled.


Hi,

Thank you for telling me about the change :D

-Ash R

---

### Post by TopFan on 2009-06-14
> **fooman said:**
> right click on an empty area of the top panel and choose "add to panel" from the drop-down list.

in the list that pops up,  click on "notification area",  then click "add".

see if that gets it back.

Thanks Fooman, that seems to have worked. I've got the icon back but also have 8(!) gmail notifier icons! Can't seem to get rid of them. Any ideas?

---

### Post by gradinaruvasile on 2009-06-14
Did u removed nm-applet or the whole notification area (system tray)?
Do:
Right click on the upper taskbar, click add to panel, select notification area, click add. Does the icon appear?

Sessions is Startup applications in Ubuntu 9.04

press alt+f2, and type nm-applet there 

(The code usually means something to type in a terminal by opening Applications->Accessories->Terminal and typing the code on the command line)

---

### Post by TopFan on 2009-06-14
All sorted now. I just removed Gmail notifier and the icons went. I'll re-install it later.

Much appreciated everyone. Thank you for your time.

---

