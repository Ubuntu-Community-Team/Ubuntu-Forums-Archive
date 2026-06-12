---
title: "Log On Wallpaper"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by justin43384 on 2010-09-12
I got tired of the Ubuntu log on wallpaper for a while now.  Is there any way to change it??

:D

---

### Post by Lunarmonkey on 2010-09-12
"There is a utility included with Ubuntu that allows quick and easy  customization of options within the GDM theme titled gdmsetup; you can  run this utility directly from the main menu by looking under System  -> Admin -> Login Window. You’ll need to enter your admin password to gain access, then click  on the tab labeled “Local” to see theme options. Under the section  labelled “Style” you can select one of three  main presets: Plain,  Themed or Face Browser. Select “Themed” to gain the ability to select  any graphic you like from the provided list along with several other  default GNOME themes that may suit your fancy – customization is always  great but you have to admit that the default GDM theme is a pretty  attractive piece!"


I hope this helps this isnt in my word personally but its the right way to do it.

---

### Post by Redblade20XX on 2010-09-12
Try searching for ubuntu tweak on google.

---

### Post by Capt_Scribble on 2010-09-12
I don't know why that feature was removed from the Admin menu but you can try this:
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```The window will look like the personal one, but it will change the login screen instead.

---

### Post by Capt_Scribble on 2010-09-12
> **Lunarmonkey said:**
> "There is a utility included with Ubuntu that allows quick and easy  customization of options within the GDM theme titled gdmsetup; you can  run this utility directly from the main menu by looking under System  -> Admin -> Login Window.
I don't see that option. Can it be installed?

---

### Post by Chris1274 on 2010-09-12
I did it in a roundabout way, but it works.

Go to the backgrounds directory (usr/share/backgrounds) and look for the default background image. Make a note of the file name. Let's call it "theme.jpg". Move that image out of the backgrounds directory.

Change the name of your preferred background image to "theme.jpg" and move it into /usr/share/backgrounds.

Next time you reboot, your preferred image should show up as the background on the login screen.

---

### Post by Lunarmonkey on 2010-09-13
> **Capt_Scribble said:**
> I don't see that option. Can it be installed?
It should already be installed, other then that i cant relay help you with it other then doing what the others have said to do.

---

### Post by 3rdalbum on 2010-09-13
> **Lunarmonkey said:**
> It should already be installed, other then that i cant relay help you with it other then doing what the others have said to do.

It only works with Ubuntu 9.04's and earlier. After that they rewrite GDM.

---

### Post by Capt_Scribble on 2010-09-13
> **Lunarmonkey said:**
> It should already be installed, other then that i cant relay help you with it other then doing what the others have said to do.I see you're using Lucid as well. Did it auto install for you? How did you get it?

---

### Post by opendevlite on 2010-09-13
i use ubuntu tweak to do this

---

### Post by Lunarmonkey on 2010-09-13
> **3rdalbum said:**
> It only works with Ubuntu 9.04's and earlier. After that they rewrite GDM.
I know i posted that option because he is using 10.04

And yes it was pre installed it may come up as login screen
so try System  -> Admin -> Login screen and then fallow the steps

---

### Post by justin43384 on 2010-09-13
Thank You!!! It works when you use Ubuntu Tweaks!!
:KS:popcorn:):P:popcorn::lolflag::guitar::D

---

