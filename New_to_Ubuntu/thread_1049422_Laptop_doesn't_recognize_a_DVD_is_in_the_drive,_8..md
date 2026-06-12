---
title: "Laptop doesn't recognize a DVD is in the drive, 8.10"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by lokesvara on 2009-01-24
Hi, all! Really loving Intrepid Ibex on this IBM T40 Thinkpad I got on the cheap. Ideally I'd like to travel with this laptop, since it cost me next to nothing and is fairly slim and light (certainly for its age)...

But I'm having a problem, and I hope that someone can help. I've been browsing the forums for a while, reading about some of the basic things that must be done in order to play DVDs in Ubuntu:

--I added Medibuntu to the list of sites from which I can download packages.
--I installed libdvdcss2, vlc, totem-xine, etc. etc. I don't remember everything to be honest, but can look up and post anything that will help!

The DVD/CDRW drive itself seems to be recognized by Ubuntu, as I can play and even burn CDs no problem. Here's what I get back from lshw -class disk (short and long output):

H/W path           Device      Class          Description
=========================================================
/0/100/1f.1/1      /dev/cdrom  disk           UJDA745 DVD/CDRW

  *-cdrom
       description: DVD reader
       product: UJDA745 DVD/CDRW
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.03
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc

Links all appear to be correct:
/dev$ ls -l|grep cd
lrwxrwxrwx  1 root   root           4 2009-01-19 21:55 cdrom -> scd0
lrwxrwxrwx  1 root   root           4 2009-01-19 21:55 cdrw -> scd0
lrwxrwxrwx  1 root   root           4 2009-01-19 21:55 dvd -> scd0
brw-rw----+ 1 root   cdrom    11,   0 2009-01-19 21:55 scd0
crw-rw----  1 root   cdrom    21,   1 2009-01-19 21:55 sg1
lrwxrwxrwx  1 root   root           4 2009-01-19 21:55 sr0 -> scd0

However, for example VLC will return the following if I insert and then try to play a DVD. The other multimedia players all give similar responses:

[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: vm: failed to open/read the DVD
[00000409] dvdread demux error: DVDRead cannot open source: /dev/scd0
[00000412] main access error: no access module matched "dvd"
[00000408] main input error: open of `dvd:///dev/scd0' failed: could not create access: no access module matched "dvd"

Am I missing something? Please let me know.

Thanks!

---

### Post by jimmy the saint on 2009-01-24
Did you try it with another DVD?  I ran into a DVD that wouldn't open and I am pretty sure it was a DRM issue.  I didn't investigate further, but that was my assumption.

---

### Post by lokesvara on 2009-01-24
> **jimmy the saint said:**
> Did you try it with another DVD?  I ran into a DVD that wouldn't open and I am pretty sure it was a DRM issue.  I didn't investigate further, but that was my assumption.

Unfortunately, none of the handful of titles I tried were recognized. :(

---

### Post by golusweet on 2009-01-24
Just use VLC player.:D

---

### Post by lokesvara on 2009-01-25
> **golusweet said:**
> Just use VLC player.:D

Thanks, but VLC was one of the players I tried--some of the output is at the end of my first post.

I also tried Totem and gxine...

---

