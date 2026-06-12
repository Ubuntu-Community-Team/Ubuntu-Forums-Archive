---
title: "Add Set of Wallpapers together?"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by WubiAR on 2011-07-15
Hello there,

I would like to know how you setup a bunch of wallpapers together (there are some in the default Ubuntu OS) so that they switch one after the other?

---

### Post by GWBouge on 2011-07-15
I use a cron task to call this script every 20 minutes to change the background at random:

[http://sourceforge.net/projects/gbswitcher/]("http://sourceforge.net/projects/gbswitcher/")

---

### Post by jtarin on 2011-07-15
Desktop Drapes and desktop-nova,both in the repositories and easy to setup.

---

### Post by mcduck on 2011-07-15
Gnome allows you to create wallpaper slide shows by making a simple XML file that lists all the images and how long each should show (or fade to the next image). Then just add that XML file as wallpaper like you would add a single image (remember to set the file selection dialog to show all files instead of images if you want to browse to the XML file instead off )

You can use the pre-made ones as reference, you'll find them in /usr/share/backgrounds.

I believe there is also some graphical tool made for creating such slide shows, but I've never bothered using it so I can't remember it's name. Worth searching for, though, if you feel uncomfortable working with text-based config files. :)

---

### Post by WubiAR on 2011-07-15
Why can't I create a folder in usr/share/backgrounds? I try to right click but the option is inactive for creating one.

---

### Post by CatKiller on 2011-07-15
> **WubiAR said:**
> Why can't I create a folder in usr/share/backgrounds?

Because you don't own it.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dcsoldschool53 on 2011-07-15
> **WubiAR said:**
> Why can't I create a folder in usr/share/backgrounds? I try to right click but the option is inactive for creating one.
In a terminal,type this```
gksu nautilus /usr/share/backgrounds
```to open the backgrounds folder, so that you can create a new  folder. ```
[http://ubuntuforums.org/showthread.php?p=8754415](http://ubuntuforums.org/showthread.php?p=8754415)
``````
[http://www.linuxjournal.com/content/create-custom-transitioning-background-your-gnome-228-desktop](http://www.linuxjournal.com/content/create-custom-transitioning-background-your-gnome-228-desktop)
```

---

### Post by dcsoldschool53 on 2011-07-15
> **WubiAR said:**
> Hello there,

I would like to know how you setup a bunch of wallpapers together (there are some in the default Ubuntu OS) so that they switch one after the other?

There is a program called Crebs that you can use to create a wallpaper slide show. The following two web sites are for crebs for natty and 10.10/10.04:

Natty
[http://www.liberiangeek.net/2011/04/create-background-slideshows-ubuntu-11-04-natty-narwhal-crebs/](http://www.liberiangeek.net/2011/04/create-background-slideshows-ubuntu-11-04-natty-narwhal-crebs/)

Maverick/Lucid
[http://www.liberiangeek.net/2010/09/create-background-slideshows-crebs-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/create-background-slideshows-crebs-ubuntu-10-0410-10-maverick-meerkat/)

---

### Post by Jacobonbuntu on 2011-07-15
> **WubiAR said:**
> Why can't I create a folder in usr/share/backgrounds? I try to right click but the option is inactive for creating one.

You can install nautilus extensions, it makes it very easy; after installation, you can just right-click on the usr/share/backgrounds -icon and choose "open as administrator". Then you can do anything in the folder untill you close it.

Be careful of course in wat you do :)

---

### Post by fooman on 2011-07-15
> **dcsoldschool53 said:**
> There is a program called Crebs that you can use to create a wallpaper slide show. The following two web sites are for crebs for natty and 10.10/10.04:

Natty
[http://www.liberiangeek.net/2011/04/create-background-slideshows-ubuntu-11-04-natty-narwhal-crebs/](http://www.liberiangeek.net/2011/04/create-background-slideshows-ubuntu-11-04-natty-narwhal-crebs/)

Maverick/Lucid
[http://www.liberiangeek.net/2010/09/create-background-slideshows-crebs-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/create-background-slideshows-crebs-ubuntu-10-0410-10-maverick-meerkat/)

nice one!!  

that makes it easy!

---

