---
title: "BASH : Cutting a MP3 using its CUE file ?"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by honeybear on 2010-11-27
Hi, regarding MP3, with a given  CUE file , can one cut the MP3 so that it creates a multiple of MP3 files ? 

Cheers

---

### Post by mikewhatever on 2010-11-28
Haven't tested it, but looks promising.
[http://aidanjm.wordpress.com/2007/01/18/splitting-mp3-by-cue-file-under-ubuntu-linux/](http://aidanjm.wordpress.com/2007/01/18/splitting-mp3-by-cue-file-under-ubuntu-linux/)

> **Splitting mp3 by cue file in ubuntu**

Use mp3splt to break up an mp3 file according to the break points contained in a cue file. To install mp3splt open a terminal window and enter the following:

**sudo aptitude install mp3splt**

To split an mp3 file named “music.mp3&#8243; using a cue file named “music.cue” issue the following in a terminal window:
[B]
mp3splt -c music.cue music.mp3[/B]

---

### Post by honeybear on 2010-11-28
> **mikewhatever said:**
> Haven't tested it, but looks promising.
[http://aidanjm.wordpress.com/2007/01/18/splitting-mp3-by-cue-file-under-ubuntu-linux/](http://aidanjm.wordpress.com/2007/01/18/splitting-mp3-by-cue-file-under-ubuntu-linux/)

```
apt-get install mp3splt
```

> mp3splt 2.2.5 (16/05/09) - using libmp3splt 0.5.6
        Matteo Trotta <mtrotta AT users.sourceforge.net>
        Alexandru Munteanu <io_fx AT yahoo.fr>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!

worked very well ! many thanks !!

> 
 Processed 137959 frames - Sync errors: 0
 file split (EOF)

 +-----------------------------------------------------------------------------+
 |NOTE: When you use cddb/cue, split files might be not very precise due to:|
 |1) Who extracts CD tracks might use "Remove silence" option. This means that |
 |   the large mp3 file is shorter than CD Total time. Never use this option.  |
 |2) Who burns CD might add extra pause seconds between tracks.  Never do it.  |
 |3) Encoders might add some padding frames so  that  file is longer than CD.  |
 |4) There are several entries of the same cd on CDDB, find the best for yours.|
 |   Usually you can find the correct splitpoints, so good luck!  |
 +-----------------------------------------------------------------------------+
 | TRY TO ADJUST SPLITS POINT WITH -a OPTION. Read man page for more details!  |
 +--------------------------------------------------------



---

### Post by vfikov on 2012-09-04
Hey guys!
Greetz from Bulgaria.
I just wanted to say thanks to mikewhatever for the easyest way for splitting one mp3 (with cue) to individual song in just a few seconds!
:guitar:
Best regards,
Valeri Fikov

---

### Post by sisco311 on 2012-09-04
[[img]http://ompldr.org/tYnpyNw[/img]](http://ompldr.org/vYnpyNw)

---

