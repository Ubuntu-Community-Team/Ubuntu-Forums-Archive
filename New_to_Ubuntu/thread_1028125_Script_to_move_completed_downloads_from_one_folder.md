---
title: "Script to move completed downloads from one folder to another?"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by tododo on 2009-01-02
Hi 
Just trying to figure out if there is a way to write a little script to move all finished newgroups downloads for a particular tv series for example to shared samba folder of a similar name

I have in use at the moment


#!/bin/sh
cd /media/500gbShare/UbuntuShares/NewsgroupDownloads/FinishedDownloads/TV/
find . -iname '*rub*' -exec mv -v {} /media/500gbShare/UbuntuShares/SharedVideos/SharedTVShows/Scrubstest/ \;

This moves files which contain rub (as in scrubs) from the TV folder to a folder on a samba shared called Scrubstest folder

Is this the best way of doing it?

Problem I seem to have with the above is that it doesnt just move the video but also the folder that the video is in

Is there any easier solution......please remember Im not a unix guru just trying to learn a bit :)

Thanks for any advice 

As i will be having a number of tv shows downloaded I guess i will need a separate script for each one

---

### Post by bluefrog on 2009-01-02
find . -type f -iname '*scrub*'  to restrict the search to files not directory

---

### Post by tododo on 2009-01-02
arhhaha brill thanks

Probably getting a bit more complicated now but is there then anyway to do the above and then delete the folder where the file was moved from???

---

### Post by wmdiem on 2009-01-02
> **tododo said:**
> Hi 

As i will be having a number of tv shows downloaded I guess i will need a separate script for each one
 Or you could have it take an argument [http://www.comptechdoc.org/os/linux/programming/script/linux_pgscriptvariables.html](http://www.comptechdoc.org/os/linux/programming/script/linux_pgscriptvariables.html)
So you set it up to look in a particular directory, and move to a particular directory, but tell it at runtime what to search for.
something like 
```
#!/bin/sh
cd /media/500gbShare/UbuntuShares/NewsgroupDownloads/FinishedDownloads/TV/
find . -iname '*$1*' -exec mv -v {} /media/500gbShare/UbuntuShares/SharedVideos/SharedTVShows/$1/ \;
```

---

### Post by tododo on 2009-01-02
Brill thanks guys

Will have a look at these variables.....need to dip my feet in :)

---

