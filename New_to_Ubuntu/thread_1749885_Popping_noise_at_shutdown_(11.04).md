---
title: "Popping noise at shutdown (11.04)"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by rojodojo on 2011-05-05
Hi,

I recently installed the latest version of Ubuntu, and whenever the system shuts down, there is a loud popping noise coming out of the speakers. This bug is similar to that which plagued 9.10, but the tutorials for fixes in that version do not seem to apply to 11.04.

If anyone has had this problem or knows of what could be done to fix it, feedback would be great,

Thanks in advance

---

### Post by madjr on 2011-05-05
hi,

can you link those tutorials?

also have you found or reported this bug recently ?

---

### Post by EGamerHDK on 2011-05-05
I'm on a laptop and when using the built in speakers I do not get a loud pop when I shutdown, but I have a 1000 Watt Audio System that I connect via an external USB audio card and if I have it plugged in at the time of shutdown I do get a pop (from the audio system). 

I also get this pop at start-up with Ubuntu. 

I have come to terms with it because usually the volume is turned up about halfway and I just feel like once the speakers initially receive an input or lose an input they pop. Just like if I plug my MP3 player into my speakers or unplug it.

My questions are:

1. Are you using some sort of sound card/external speakers (Not sure if you're on a desktop/laptop as you didn't provide any system info)

2. Do you get this at start-up?

---

### Post by rojodojo on 2011-05-09
To the madjr, this is [an example of a tutorial]("http://www.webupd8.org/2009/10/fixing-popping-sound-in-ubuntu-karmic.html") for an audio fix in karmic. And I will report a bug as soon as I figure out how to do so.

To EGamerHDK, I'm just using the built-in Altec Lansing laptop speakers of my laptop. And yes, I get popping on boot up, shut down, hibernate, wake-up etc. Basically, whenever the computer spins down, or up I get an annoying popping.

---

### Post by madjr on 2011-05-10
> **rojodojo said:**
> To the madjr, this is [an example of a tutorial]("http://www.webupd8.org/2009/10/fixing-popping-sound-in-ubuntu-karmic.html") for an audio fix in karmic. And I will report a bug as soon as I figure out how to do so.

To EGamerHDK, I'm just using the built-in Altec Lansing laptop speakers of my laptop. And yes, I get popping on boot up, shut down, hibernate, wake-up etc. Basically, whenever the computer spins down, or up I get an annoying popping.

this is how you can report them:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by wilhelmschumann on 2011-05-21
I have Upgraded some packages on My laptop ( HP Pavilion DV 9000 ) and that annoying popping noise has stopped .
 I think is something related with Xorg, Xorgserver or X11.

Cheers!

Those Packages updated are:


Upgraded the following packages:
apturl (0.4.2ubuntu5) to 0.4.2ubuntu5.1
apturl-common (0.4.2ubuntu5) to 0.4.2ubuntu5.1
firefox (4.0.1+build1+nobinonly-0ubuntu0.11.04.2) to 4.0.1+build1+nobinonly-0ubuntu0.11.04.3
firefox-gnome-support (4.0.1+build1+nobinonly-0ubuntu0.11.04.2) to 4.0.1+build1+nobinonly-0ubuntu0.11.04.3
flashplugin-installer (10.2.159.1ubuntu1) to 10.3.181.14ubuntu0.11.04.1
geoclue (0.12.0-1ubuntu8) to 0.12.0-1ubuntu8.1
gnome-nettool (2.32.0-0ubuntu1) to 2.32.0-0ubuntu1.1
im-switch (1.20ubuntu3) to 1.20ubuntu3.1
language-pack-en (1:11.04+20110421) to 1:11.04+20110509
language-pack-gnome-en (1:11.04+20110421) to 1:11.04+20110509
language-selector-common (0.34) to 0.34.2
language-selector-gnome (0.34) to 0.34.2
libgeoclue0 (0.12.0-1ubuntu8) to 0.12.0-1ubuntu8.1
libntrack-qt4-1 (011-1ubuntu1) to 011-1ubuntu1.1
libntrack0 (011-1ubuntu1) to 011-1ubuntu1.1
libtelepathy-logger2 (0.2.6-1ubuntu1) to 0.2.6-1ubuntu1.2
ntrack-module-libnl-0 (011-1ubuntu1) to 011-1ubuntu1.1
python-papyon (0.5.5-1ubuntu1.1) to 0.5.5-1ubuntu1.2
software-center (4.0.1) to 4.0.2
telepathy-logger (0.2.6-1ubuntu1) to 0.2.6-1ubuntu1.2
x11-common (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xorg (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xorg-dev (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xserver-common (2:1.10.1-1ubuntu1) to 2:1.10.1-1ubuntu1.1
xserver-xorg (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xserver-xorg-core (2:1.10.1-1ubuntu1) to 2:1.10.1-1ubuntu1.1
xserver-xorg-dev (2:1.10.1-1ubuntu1) to 2:1.10.1-1ubuntu1.1
xserver-xorg-input-all (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xserver-xorg-video-all (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1

---

### Post by rojodojo on 2011-06-02
> **wilhelmschumann said:**
> I have Upgraded some packages on My laptop ( HP Pavilion DV 9000 ) and that annoying popping noise has stopped .
 I think is something related with Xorg, Xorgserver or X11.

Cheers!

Those Packages updated are:


Upgraded the following packages:
apturl (0.4.2ubuntu5) to 0.4.2ubuntu5.1
apturl-common (0.4.2ubuntu5) to 0.4.2ubuntu5.1
firefox (4.0.1+build1+nobinonly-0ubuntu0.11.04.2) to 4.0.1+build1+nobinonly-0ubuntu0.11.04.3
firefox-gnome-support (4.0.1+build1+nobinonly-0ubuntu0.11.04.2) to 4.0.1+build1+nobinonly-0ubuntu0.11.04.3
flashplugin-installer (10.2.159.1ubuntu1) to 10.3.181.14ubuntu0.11.04.1
geoclue (0.12.0-1ubuntu8) to 0.12.0-1ubuntu8.1
gnome-nettool (2.32.0-0ubuntu1) to 2.32.0-0ubuntu1.1
im-switch (1.20ubuntu3) to 1.20ubuntu3.1
language-pack-en (1:11.04+20110421) to 1:11.04+20110509
language-pack-gnome-en (1:11.04+20110421) to 1:11.04+20110509
language-selector-common (0.34) to 0.34.2
language-selector-gnome (0.34) to 0.34.2
libgeoclue0 (0.12.0-1ubuntu8) to 0.12.0-1ubuntu8.1
libntrack-qt4-1 (011-1ubuntu1) to 011-1ubuntu1.1
libntrack0 (011-1ubuntu1) to 011-1ubuntu1.1
libtelepathy-logger2 (0.2.6-1ubuntu1) to 0.2.6-1ubuntu1.2
ntrack-module-libnl-0 (011-1ubuntu1) to 011-1ubuntu1.1
python-papyon (0.5.5-1ubuntu1.1) to 0.5.5-1ubuntu1.2
software-center (4.0.1) to 4.0.2
telepathy-logger (0.2.6-1ubuntu1) to 0.2.6-1ubuntu1.2
x11-common (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xorg (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xorg-dev (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xserver-common (2:1.10.1-1ubuntu1) to 2:1.10.1-1ubuntu1.1
xserver-xorg (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xserver-xorg-core (2:1.10.1-1ubuntu1) to 2:1.10.1-1ubuntu1.1
xserver-xorg-dev (2:1.10.1-1ubuntu1) to 2:1.10.1-1ubuntu1.1
xserver-xorg-input-all (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xserver-xorg-video-all (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1

Did you just use a system update? Or did you do something in the terminal to update those packages?

I recently reformatted and fully updated everything via system update, however I still get the pop. [These guys are also having the same problem]("http://ubuntuforums.org/showthread.php?t=1748115").

---

### Post by murmilad on 2011-10-21
You can find some solution [here]("http://ubuntuforums.org/showthread.php?p=11377449#post11377449") :)

---

