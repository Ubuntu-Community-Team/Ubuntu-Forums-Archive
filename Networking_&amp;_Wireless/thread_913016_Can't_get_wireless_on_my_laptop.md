---
title: "Can't get wireless on my laptop"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by daimere on 2008-09-07
I uploaded Ubuntu to my laptop that was showing the NTDLR error because reformatting had an error and didn't load correctly.  

When I installed it at first, it would not let me connect to internet through wireless or wired.  I made sure the wireless card is on, I've used [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102") that thread which let it work wired but still not wireless.  

I tried troubleshooting and it wouldn't let me do it.  This was the last screen shot of my terminal I had trying to troubleshoot with that:
[IMG]http://i28.photobucket.com/albums/c207/daimere/Screenshot-1.png[/IMG]

---

### Post by daimere on 2008-09-12
Can anyone figure out this problem?

---

### Post by TSupra88 on 2008-09-12
try this: [http://tsupra88.blogspot.com](http://tsupra88.blogspot.com)

(I've written a quick, but clear tutorial that will help you install broadcom cards and I've provided links to the necessary drivers/firmware.)

---

### Post by Kevbert on 2008-09-12
You need to install firmware drivers which will be saved in the /lib/firmware directory.  You can do this via this [[COLOR="Red"]post.[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13")

---

### Post by daimere on 2008-09-12
[IMG]http://i28.photobucket.com/albums/c207/daimere/Screenshot-shannonshannon-laptop.png[/IMG]

Iwas doing the Tech and More one.  I got that far till it said that stuff.  It has made my wireless symbol light up!  That is the only way I know that it started working!

---

### Post by Kevbert on 2008-09-12
The reason you got permission denied is that you need root permissions to use those commands - use either sudo at the start of each command or
```
sudo su
```
to give root permissions to all commands (for the session).

---

### Post by daimere on 2008-09-12
[IMG]http://i28.photobucket.com/albums/c207/daimere/222.png[/IMG]

sudo su didn't work

---

### Post by Kevbert on 2008-09-13
Sorry, I wasn't clear enough.  If you enter
```
sudo su
```
in terminal on its' own and then enter all the other commands in new lines afterwards you should get access.

---

### Post by jualin on 2008-09-13
If you don't get your wireless card to work using the linux native drivers (bcm43xx) you can try using Windows drivers by using Ndiswrapper alternative. You can follow the link on my signature for a tutorial. Usually the first step is identifying your wireless card by going to the terminal and typing > lspci and your wireless card should be the one that says "Broadcom <model goes here>" (assuming that you have a Broadcom chipset). If you have trouble finding the Windows drivers [this website]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/") has the drivers and specific information for many wireless cards. Good luck!

---

### Post by daimere on 2008-09-13
Okay. SO I did the black list stuff and I don't see any change.  Unless there is some ubunto/linux supa power that I don't know to make it connect to my wireless network.  I just unplugged it and watched if my internet would work.

---

