---
title: "dvd image ripping"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Periswell on 2009-03-03
hello

i have a dvd image (iso) file on my computer of one of my dvds so that if it brakes, all is not lost. Thusly the dvd did brake. i noticed the iso cannot be played by any player (vlc, xine, mythtv) they all just crash. I want to rip a video (eg avi) file from the dvd image. i went to use k9copy but when it starts ripping, it crashes. I also tried acidrip but that cannot distinguish between the different titles so it all gets ripped including dvd menues. this is just a snippet of what k9copies output was in the terminal:
> *** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
[libdvdnav: Using dvdnav version 1.2.3 from [http://xine.sf.net](http://xine.sf.net)
]
[NAME OPEN FAILED
]
[libdvdnav: Unable to find map file '/home/joshua/.dvdnav/.map'
]
[libdvdnav: DVD disk reports itself with Region mask 0x00ed0000. Regions:]
[ 2]
[ 5]
[
]
[libdvdread: Invalid IFO for title 11 (VTS_11_0.IFO).
]
[libdvdnav: ifoOpenVTSI failed
]
[libdvdnav: *** pgci_ut handle is NULL ***
]
[KCrash: Application 'k9copy' crashing...
]
[============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.
]
joshua@joshua-laptop:~$ 

And thoughts to the matter? thanks in advance.

-Joshua

---

### Post by DGortze380 on 2009-03-03
> **Periswell said:**
> hello

i have a dvd image (iso) file on my computer of one of my dvds so that if it brakes, all is not lost. Thusly the dvd did brake. i noticed the iso cannot be played by any player (vlc, xine, mythtv) they all just crash. I want to rip a video (eg avi) file from the dvd image. i went to use k9copy but when it starts ripping, it crashes. I also tried acidrip but that cannot distinguish between the different titles so it all gets ripped including dvd menues. this is just a snippet of what k9copies output was in the terminal:

And thoughts to the matter? thanks in advance.

-Joshua

If it's just an avi on a DVD, why do you need to rip it?
Mount the image, copy the file.

Now if it's a commercial dvd with a Video_ folder, that's a little different and you'll need to rip it.

---

### Post by Periswell on 2009-03-03
ok i think i have not made myself so clear

1,iso of casino royale on laptop harddrive
2,real original dvd broken
3,iso file won't play
4,file to big to put on blank dvd
5,want to take an avi movie file of the film itself (nothing more) from the iso image on my harddrive, not on second dvd.

hopefully that helped

-joshua

---

### Post by DGortze380 on 2009-03-03
> **Periswell said:**
> ok i think i have not made myself so clear

1,iso of casino royale on laptop harddrive
2,real original dvd broken
3,iso file won't play
4,file to big to put on blank dvd
5,want to take an avi movie file of the film itself (nothing more) from the iso image on my harddrive, not on second dvd.

hopefully that helped

-joshua

Are you trying to play the iso directly??

please mount the iso, navigate to the directory (commandline or GUI), and post the contents of the directory (commandline txt output or screenshot)

---

### Post by MrWES on 2009-03-03
first from the terminal:

mkdir /media/isoimage

Then install gisomount

sudo apt-get install gisomount

Now you can use gisomount to mount the iso image, and use one of several programs to create an avi file; avidemux, handbrake, etc.

Bill

---

### Post by handy on 2009-03-03
If I have an .iso I can just use NeroLinux to burn the image.

Surely the other Linux burners have the option to burn an image?

---

### Post by MrWES on 2009-03-03
> **handy said:**
> If I have an .iso I can just use NeroLinux to burn the image.

Surely the other Linux burners have the option to burn an image?

Brasero; the default burning app can burn an iso file

---

### Post by Twitch6000 on 2009-03-03
Get the 30 the trail of nero linux to rip the .iso and if it don't work the .iso is probably broke.

---

### Post by Periswell on 2009-03-05
ok first of all i  will try gisomount
secondly i cant burn it to a disk as its 8gb and i only have 4gb disks.
lastly i can't rip it again as the original disk is broken.

-joshua

---

### Post by MrWES on 2009-03-05
You mount the iso as described in previous posts using gisomount, and then use K9Copy to re-copy the disk and shrink it down to a DVD5 size.

Bill

---

### Post by linuxuser21 on 2009-03-05
DVDs often have errors on them when they are burned at a high speed.  This happens a lot especially if the DVD burner has been used a lot.  Your DVD player doesn't see the errors; however when you try to copy or rip from it, your computer cannot continue because of it.

---

