---
title: "Music CD won't play but CD ROM drive is recognized in Disk Utility"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by cnymike on 2010-09-16
I've tried playing several music CD's and they will not play.

In Storage Devices my CD ROM shows up as NEC CD-2800D, port 2 of PATS Host Adapter, No Media Detected, Device: /dev/sr0, firmware version 3.73

The Eject Media button in Storage Devices does eject the CD. But when a CD is inserted, Rhythmbox does not recognize that a CD has been inserted and Storage Devices also reports that No Media Detected.

AFAIK the drive worked perfectly under Windows ME, Windows XP.

The notebook is a really old HP Pavilion XH136, Intel Celeron 600MHz
Mem:    250612k total,   244080k used,     6532k free,     7120k buffers

Any ideas what I can try to do to get music CD's to play?

---

### Post by andrewthomas on 2010-09-16
[B]Comprehensive Multimedia & Video Howto

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[/B]

---

### Post by MooPi on 2010-09-16
Is this expressly a cd-rom or dvd device ? I recently had a similar issue involving dvd play and the device being recognized. Sadly I saved data and reinstalled because I could not find a solution. I'm curious if you are using any ppa's or medibuntu  ?  In terminal can you eject the media with ```
eject
```

---

### Post by cnymike on 2010-09-16
The CD does eject using the terminal command 'eject'

It is a CD ROM player only

In file browser, I see CD Drive and File System. When I insert a data CD, the CD  Drive reads the disc and I can view the files. When I eject the CD and insert an audio CD, the CD Drive icon disappears in the File Browser. When I eject the audio CD, the CD Drive icon reappears.

---

