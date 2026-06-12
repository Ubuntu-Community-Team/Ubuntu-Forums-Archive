---
title: "change icon"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by bu2971x on 2009-01-28
is there a special way to change a dsktp icon..?????

---

### Post by HotShotDJ on 2009-01-28
Right click on the desktop icon that you want to change... click on "Properties."  You'll see the current icon in the top-left corner of the "Basic" tab.  Click on it and then browse to the icon file that you want to use.

---

### Post by Crafty Kisses on 2009-01-28
If you're talking about changing the start icon,yes you can. So basically there is a lot of tutorials out there on how to change the Gnome-Panel icon, but a lot of them don't work with Hardy, here are a couple of good ways of approaching this.

[LIST]
[*]Manually putting them into the directory 
[*]Recreating the folder
[/LIST]
You can go into the following directory: 
```
/usr/share/icons/themename/24x24/places/start_here.png
```Once you're in there make sure you open your icon and it's scaled for 24x24. One thing you probably should do is backup the old icon, copy it and put it in a folder. So once you've done that, remove the "start-here.png" file from the directory, then rename your new logo "start-here" and put it in the directory. After that, you want to run this command:
```
sudo gtk-update-icon-cache /usr/share/icons/Human/
```After you've done that, go into Terminal and run this command:
```
killall gnome-panel
```The Gnome panel should disappear for a second and come back with your desired logo.

The simplest way to do it (and I forget which thread I read this in, but kudos to whomever suggested it first) is to create a folder in your home directory for the icon theme you use and then put your custom icon in there. One of the more simpler ways to do this (and I forget which thread I read this in, but thanks to whoever suggested it) is to create a folder in your home directory for the icon theme you use and then put your custom icon that you want to use in there. So an example would be, if you're using the Human theme create this directory:
```
/home/username/.icons/Human/scalable/places/distributor-logo.png
```Then you can run this in Terminal:
```
killall gnome-panel
```Then you should have your custom icon where the Ubuntu icon was.

---

### Post by HotShotDJ on 2009-01-28
> **Codename said:**
> Then you should have your custom icon where the Ubuntu icon was.BRILLIANT!  I just changed my Applications icon. Here it is

---

### Post by venik212 on 2009-02-26
This might have worked in previous KDEs, but seems to NOT work in KDE4.2.  It would really be nice to know how to do such a simple thing in KDE 4.2.

---

