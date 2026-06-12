---
title: "In the event of HD failure..."
date: 2009-06-03
forum: New to Ubuntu
---

### Post by mesmith on 2009-06-03
On my system, I have two hard drives.  One carries xubuntu and a swap area, the other I use for partimage backups.  Partimage backups have saved my *** numerous times.

However, in the event of a total HD failure on my main disk it seeems to me that simply popping in a new disk, formatting and partitioning it (it would no doubt be a larger disk) would leave me with a hell of a mess.  If I restored the partimage file wouldn't I have mbr, fstab, blkid.tab, etc. errors galore?  Would the best plan be to keep a backup of my /home files, do a clean install then copy over /home?  If that's the case, what's the best way to keep a copy of my /home files (including, I assume, hidden files) that they could be easily copied back after a reinstall?  something simple and straightforward, as I've only been using xubuntu 8 months.

---

### Post by candtalan on 2009-06-03
An easy way I find is to use sbackup, it is simple to configure, even just keep the defaults. I think it is in the repositories. 

For a more DIY approach I also often use rsync but this is in a terminal, for example (create the destination directory here /data-bak  first though I think. See man rsync for more details.
```

sudo rsync -rt --progress --stats -v --log-file=rsynclog.txt /data/ /data-bak/

```
hth

---

### Post by hobo14 on 2009-06-03
.... LiveCds are located under the seat in front of you.  Please exit calmly through the nearest USB port.

---

### Post by mesmith on 2009-06-05
sbackup it is.  Thanks.

---

### Post by LewRockwell on 2009-06-05
Clonezilla is what I use to make disk and partition clones

---

### Post by DBrocks on 2009-06-05
I am partial to rsync, as its much faster. The first time it runs, it will take a while. But once its done that, it does incremential backups, which means it only has to copy over the files that have been changed since the last backup. (Actually it only copies the changed bits in each individual files, so you dont even have to copy the entire file over). CLI can be intimidating with all those flags, but you could just write a launcher to do it. Not sure if sbackup does the same thing. RAID 1 also works, but the thing is, RAID is no substitute for backups, it only prevents against physical disk failures, not against accidential deletions/virii.

---

### Post by mesmith on 2009-06-06
Thanks for the good advice.  Currently, I use PartImage out to a second HD.  That's great for recovering from my own stupidity, but I needed to have my /home out on the other HD so that after a main HD replacement and clean install I could then move back ny docs, mail and desktop settings.  Sbackup seems to be a simple way to go for this application.  Thanks again.

---

