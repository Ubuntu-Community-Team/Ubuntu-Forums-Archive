---
title: "Ubuntu sound and video lag"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by einfinger on 2008-12-19
Im having some problems with a HP laptop where ive just installed 8.10 and im currently setting this up for my friend. But ive encountered some problems with the video and sound.

The sound lags and does this fast loop of whatever its playing (for instance the login screen sound) 

I tested some youtube videos and there bot video and sound does the same thing.

Ive checked hardware drivers for errors but it seems to be ok.

I dont even know where to begin with this and im grateful for any help i could get.

Thanx :)

---

### Post by Crafty Kisses on 2008-12-19
What are your system specs?

---

### Post by einfinger on 2008-12-19
whats the command for getting that info ? sudo lspci ? because i cant seem to make sense of that :P
the machine is a hp pavillion dv7 1080eo

---

### Post by einfinger on 2008-12-19
intel 82801 ich9 family hd audio controller

---

### Post by einfinger on 2008-12-19
bump

---

### Post by ohingst on 2008-12-25
Hi,

I have a DV7-1004ea.  The sound chip you mentioned is the same one as mine.
The sound issue was resolved on my system by adding the following line in the file "alsa-base" found in /etc/modprobe.d.
Use the following command to edit it:

sudo nano -w /etc/modprobe.d/alsa-base

And add the following line to the bottom of the file:

options snd-hda-intel enable_msi=1

You can unload all the ALSA sound kernel modules using "rrmod" but it is easier to restart the machine . :)

---

