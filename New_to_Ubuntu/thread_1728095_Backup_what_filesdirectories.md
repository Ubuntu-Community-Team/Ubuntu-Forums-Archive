---
title: "Backup what files/directories?"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by CVGH on 2011-04-13
I've got a hd with overlapping partitions and before I mess with it, 
I'd like to do a backup in case I have to wipe the Linux partition. 
I've tried remastersys, but the iso it made would not boot correctly.
I just got sbackup installed and am wondering what do I need to backup?
/home and /etc are what I'm thinking. Anything else?

Thanks,

Brian

---

### Post by psusi on 2011-04-13
All of your personal files should be in /home, and system settings in /etc, so if you back those two up, then you can reinstall the rest.

---

### Post by seawolf167 on 2011-04-13
Here is a [how-to ]("https://help.ubuntu.com/community/BackupYourSystem")for backing up ([with rsync]("https://help.ubuntu.com/community/rsync")).

I also like [Clonezilla ]("http://www.clonezilla.org")as you can image your entire drive and restore everything if need be

---

