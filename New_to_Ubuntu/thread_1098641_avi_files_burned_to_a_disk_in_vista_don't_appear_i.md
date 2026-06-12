---
title: "avi files burned to a disk in vista don't appear in ubuntu"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by ni ni on 2009-03-17
Hello All!

I was wondering: avi files burned to a disk in vista don't appear in ubuntu (or xp for that matter).

Is there a way around this?

---

### Post by philinux on 2009-03-17
> **ni ni said:**
> Hello All!

I was wondering: avi files burned to a disk in vista don't appear in ubuntu (or xp for that matter).

Is there a way around this?

I've a feeling it's Vista omnipotence to media.

---

### Post by Eisenwinter on 2009-03-17
Did you properly mount the cd drive?

Try this: ```
mkdir ~/MountPoint && sudo mount /dev/scd0 ~/MountPoint
```

Report results.

---

### Post by ni ni on 2009-03-17
Yes the drive works fine, i've watched xp-burned disks on it.

---

### Post by D3ath on 2009-03-17
Hey there did you install the package ubuntu-restricted-extras?  That's the first thing i do for any type of dvd or file type playback!  O and you are using VLC right? 

You can also download this: 
[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/) there is a dev version and stable i suggest stable and that works as well to install some css libs. Maybe that will work these are the best suggestions i have at the moment.

UPDATE:  Sorry I missed the note that said it wouldn't work in XP either. Maybe there is some setting in vista so that the avi isn't proprietary. Sorry my suggestions probally won't help. This does look like a issue with vista that you would have to change.

---

### Post by aeiah on 2009-03-17
if your windows xp machine cant read the disks and niether can your ubuntu one, then its gonna be a vista problem. i guess you should ask on a vista forum

---

### Post by ni ni on 2009-03-17
thanks aeiah and D3ath, i think ye are right and that it is a vista problem



thanks anyway x x x x:KS:KS:KS

---

### Post by mikechant on 2009-03-17
Possibly you need to use the 'finalize disc' function in Vista (can't remember where this is though). Some discs can't be read in other OSs until they are finalized.

---

### Post by SunnyRabbiera on 2009-03-17
also tere is the issue of DRM...
Vista is a DRM nightmare.

---

### Post by ni ni on 2009-03-17
oh that is a good idea about the finalization.  they work in normal tv dvd players though.  okay i'll get to a vista pc and try that... eeewwww vista!

kisses x x x x

---

### Post by Yashiro on 2009-03-17
[http://ubuntuforums.org/showpost.php?p=6788603&postcount=15](http://ubuntuforums.org/showpost.php?p=6788603&postcount=15)

---

