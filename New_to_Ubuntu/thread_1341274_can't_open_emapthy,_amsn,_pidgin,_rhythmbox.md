---
title: "can't open emapthy, amsn, pidgin, rhythmbox"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by quinnten83 on 2009-11-29
Okay, 
I installed open-shot throuhg the openshot ppa.
I know, but JT assured that the new ppa would play nice with VLC, and it does.
But now, a whole bunch of stuff that needs to connect me to the internet now won't start. amsn, empathy, rhythmbox and pidgin, they all crash when I run them. Skype works like crap too, with messages not getting delivered.
```
Running them from terminal keeps getting me this error:
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
Error re-scanning registry , child terminated by signal
```

aMSN specifically gives me this error:
```
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal
```

I am not quite sure that this is because of openshot, but it was the only thing that was changed on my system and after a reboot (the freezing still happens on my system apparently) the programs no longer will connect.
Also there is no folder /usr/share/opencv.

So, 
is this related to the installation of openshot?
Can I reinstall Gstreamer or is it just easier to reinstalle the system? I have a separate home partition so reinstall is no biggie.
Should I contact JT to tell him that his repo's are messing with other programs (Again!)?
I allready tried with sudo apt-get install gstreamer, that didn't work...


I don't want this guys awesome program to be associated only with troublesome PPA's, but I really do not know how to go about this...

---

### Post by Meanderer on 2009-11-30
I've got exactly the same problem and I'm a newbie to Ubuntu.
My symptoms are that aMSN trys to open but fails to complete. The same thing happens when I try to open UBUNTU SOFTWARE CENTRE. I tried opening in A Terminal Window and got exactly the same messages as you did.
My problem happened after I tried to install (1) **OPEN MOVIE EDITOR** and (2) **Kdenlive** (Video editor).
One or both have conflicted (overwritten) the registry where GStreamer should reside.

I need some advice before I go messing too much.

Thx in advance.

EDIT: Well it took me days to get my main issue fixed. I had to uninstall the two Movie Editing Software mentioned above. The real change/fix took place when I used the Repair Damaged or Broken Packages from the Grub menu. i had done this previously but it didn't find any trouble. But once I removed these programs and did it, all was operational again. :)

---

### Post by Meanderer on 2009-12-05
Well what I'd said in my previous post didn't work. BUT the following did work and I'm so relieved after a week of frustration!

> sudo apt-get remove frei0r-plugins
Woohoo . Grrrr8 :D

---

### Post by quinnten83 on 2010-01-18
Guess what, 
today after an update, I get the same issue.
I can play movie formats without a problem, but none of my IM's work.
I get the same error message as last time.
Openshot is NOT installed on this computer.
I solved the problem last time, by reinstalling, but I really don't feel like reinstalling again. So does anyone have a solution that I can easily implement?

---

### Post by bswilson on 2010-01-27
I also had this problem, and removing **frei0r-plugins** fixed me right up.  Boy, was I getting frustrated!  I basically couldn't start any program that had a Gstreamer dependancy.  I jettisoned OpenShot too, just because I was pissed at it for messing up my system...

---

