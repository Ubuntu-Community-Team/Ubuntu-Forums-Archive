---
title: "Trouble with Flash!"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by gjoellee on 2010-01-01
Flash does not work even though it is installed. I am running on 64 bit Karmic if anyone wonders.

---

### Post by Zeedok on 2010-01-01
I'm no expert, but are you running the 64bit version of the flash player?  The 32bit one doesn't work apparently.

Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1356745"), which includes instructions on installing the 64bit version.

---

### Post by gjoellee on 2010-01-01
> **Zeedok said:**
> I'm no expert, but are you running the 64bit version of the flash player?  The 32bit one doesn't work apparently.

I installed flash from the repo, so i guess it is 64 bit flash.

---

### Post by gjoellee on 2010-01-01
Solved! Using this flash: [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

---

### Post by LuisGMarine on 2010-01-01
First remove all flash packages that you installed through the repos. Easiest way is to open up Ubuntu Software Center, and type in flash in the query and uninstall those packages that are on your system. 

Or you can do it more in depth, and manually by typing these commands into a terminal.

```
sudo apt-get remove --purge flashplugin-installer
```
```
rm -f ~/.mozilla/plugins/libflashplayer.so
```
```
rm -f /usr/lib/flashplugin-installer/libflashplayer.so
```
```
rm -f /usr/lib/adobe-flashplugin/libflashplayer.so

```

Then head over to this website and follow the instructions.  There is a user on here that made a script for this, but I can't seem to pin it down.  Essentially this website shows you how to do the same thing just manually.

[http://humphreybc.wordpress.com/2009/12/09/install-the-new-64-bit-flash-in-ubuntu/]("http://humphreybc.wordpress.com/2009/12/09/install-the-new-64-bit-flash-in-ubuntu/")

In a nutshell, you are going to download the plugin.  Extract it to your computer and copy it over to the folders where we just removed them up top :lolflag:

---

