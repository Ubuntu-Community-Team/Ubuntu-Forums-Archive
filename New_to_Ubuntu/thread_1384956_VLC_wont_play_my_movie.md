---
title: "VLC wont play my movie"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by pfeifferock on 2010-01-19
I am trying to play a video that was just taken from a DVD u know like a TS file and vlc will bring up the menu screen fine but when it gets to the video it will only play maybe 3 seconds of it before the video and audio stop but the bar on the bottom saying how fast the movie is going will go in fast forward. 
-Matt

---

### Post by KeLa on 2010-01-19
What movie?
Is DVD made by Sony?
At least "007 Casino Royale" can't be played from ripped file because of Sony's special copy  protection. Playing directly from DVD works.

---

### Post by SPazzo on 2010-01-19
> **KeLa said:**
> What movie?
Is DVD made by Sony?
At least "007 Casino Royale" can't be played from ripped file because of Sony's special copy  protection. Playing directly from DVD works.

Also, some of the newer Lions Gate movies have that problem.  With one of our computers I can't even play the DVD. :o (Let alone copy it).  So, what movie is it?  Also, what did you use to copy it?

---

### Post by SteveNorman on 2010-01-19
I use vobcopy to rip, then play the results with vlc.

[http://www.toastboy.com/main/unixlinux/using-vobcopy-and-mkisofs-to-backup-dvds-to-harddrive/](http://www.toastboy.com/main/unixlinux/using-vobcopy-and-mkisofs-to-backup-dvds-to-harddrive/)

---

### Post by dirtrider1 on 2010-01-19
Have you tried playing it from the dvd itself,to play encrypted dvds youll need to add the ubuntu-restricted-extras package from the repository ,then add the medibuntu repository and install libdvdcss2 and w32codecs for 32bit or w64codecs for 64 bit and if all else fails change the video output to x-11 in vlc and it should play.

---

### Post by pfeifferock on 2010-01-21
I don't have the DVD anymore it was an independently made documentary from the 90s. VLC is already set to output x-11 because when i updated to Koala the colors got screwed up. 
-Matt

---

### Post by andrew.46 on 2010-01-22
Hi Matt,

> **pfeifferock said:**
> I don't have the DVD anymore it was an independently made documentary from the 90s. VLC is already set to output x-11 because when i updated to Koala the colors got screwed up. 

The guide you referred to had 2 steps: use vobcopy to mirror the disk and then mkisofs to create an iso. Have you tried playing the mirrored files or the iso? Best diagnostic tool is run vlc as follows:

```
cvlc -vv my_iso.iso
```

and post the output here. BTW the direction on this page:

```
mkisofs -dvd-video -o filename.iso .
```

could do with the following tweak:

```
mkisofs -dvd-video -o **[COLOR="Red"]../[/COLOR]**filename.iso .
```

Otherwise you will be building the iso in the same directory as the mirrored DVD files...

Andrew

---

