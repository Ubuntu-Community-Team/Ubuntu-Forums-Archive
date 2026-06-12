---
title: "Wallpaper Slide Show , how to easily add more photos ?"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by medya on 2010-01-15
there is a Slide-Show in the backgrounds of ubuntu, but they have a few pictures in them, I would like to add more photos 
or I would like to have 3-4 diffrent sets of slide shows to choose for my desktop wallpaper .


I know there is a way by adding photo to cosmos folder and editing the XML file by hand but isnt any other clean way to do it , without making my hand dirty?

---

### Post by bikefreakvinnie on 2010-01-15
Hi,
i did this by going to: sytem -preferences -screen savers

then for 'screensavers theme' i selected the last one which is 'pictures folder'.

If you go to: places -pictures, this screen saver setting will go thro the pictures you have in this folder..

hope that is a help...

---

### Post by bikefreakvinnie on 2010-01-15
Oh sorry thought you were talking bout screen saver not desk top background

---

### Post by cozmicharlie on 2010-01-15
> **medya said:**
> there is a Slide-Show in the backgrounds of ubuntu, but they have a few pictures in them, I would like to add more photos 
or I would like to have 3-4 diffrent sets of slide shows to choose for my desktop wallpaper .


I know there is a way by adding photo to cosmos folder and editing the XML file by hand but isnt any other clean way to do it , without making my hand dirty?

There is a nice program called Wally that should do what you want.  check it out here: 
[http://www.kabatology.com/09/09/wally-rotates-desktop-backgrounds-in-linux-windows-and-macosx/](http://www.kabatology.com/09/09/wally-rotates-desktop-backgrounds-in-linux-windows-and-macosx/)

You also might like the backgrounds from the links on the same page.  the 150 HD wallpapers and the National Geographic are real nice.

Hope this helps.

---

### Post by tellsaju on 2010-09-05
thank all
with lucid it was easy to add wally frm s/w mgr

---

### Post by williamts99 on 2010-12-06
You might want to check out [Cortina]("https://help.ubuntu.com/community/Cortina"), it even watches the folder(s) for new images.

---

### Post by Mike The KID on 2011-04-04
I'm still looking for a nice utility to do mange this but you can do it manually rather simply but editing in two locations:

```
/usr/shared/backgrounds/
```This location is basically the pictures folder where all your backgrounds are saved on your disk. The slide show is controlled by an XML file which sets picture file locations, durations, and transitions. Copy the XML as a template and you can customize your own slide show.

```
/usr/shared/gnome-background-properties/
```In this folder you'll find more XML files to use as a template. These XML files are what are loaded when you open your Display manager when you want to change your background. The XML basically defines a slide show name, location of the config xml, and language settings.

You'll need root permissions to make these changes but they're pretty simple to make. I'm still looking for a utility to that would mange this through a GUI.

---

### Post by Mike The KID on 2011-04-04
Quick update, just found this, which might more appealing to most people:

[http://www.howtogeek.com/howto/25549/how-to-create-a-wallpaper-slideshow-in-ubuntu/](http://www.howtogeek.com/howto/25549/how-to-create-a-wallpaper-slideshow-in-ubuntu/)

---

### Post by uRock on 2011-04-04
Necromancy

Thread Closed.

---

