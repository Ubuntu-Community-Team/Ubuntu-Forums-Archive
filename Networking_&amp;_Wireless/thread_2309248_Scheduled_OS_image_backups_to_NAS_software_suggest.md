---
title: "Scheduled OS image backups to NAS software suggestion"
date: 2016-01-08
forum: Networking &amp; Wireless
---

### Post by Jean_Luis on 2016-01-08
Hi, So  I tried to back up my Ubuntu partition to an HDD I have connected on my router using Clonezilla but Clonezilla apparently does not support my network card, it can never load it correctly. So I need other suggestions for this please.

I just want to backup an image of my OS (through wifi), so if anything were to happen I can revert it back to the way everything was.

Thank you.

---

### Post by TheFu on 2016-01-10
Welcome to the forums. Glad you dropped by.

I don't know how to do image-based backups that are scheduled. To get a 100% know-you-can-restore image, the OS needs to be offline, which means booting off alternate media, which means it cannot really be scheduled.  If you are willing to have a 99.995% know-you-can-restore image, there are options provided some scripting can be done.

I stopped doing image-based backups around 2005. For Linux, it just isn't necessary.  Using something like rsync or rdiff-backup or duplicity or any of the other file-based backup tools should work. Be certain you have versioned backups that can be restored from last week or the week before that or last month. Sometimes we don't realize there is an issue for many, many days so having versioned backups is absolutely critical.  Don't know how to make efficient image-based backups that are versioned. Sorry.   

When I need something like a quarterly image backup for Linux, I use fsarchive (or is it "fsarchiver"?). I don't remember. Whether this makes sense for you or not depends on many factors, with the file system used probably being the most important.  Alternate boot media is still required, so automating it really isn't possible.

rdiff-backup has been my backup tool of choice for about 6 yrs.  [https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) has a nice primer.  I do nightly, automatic, rdiff-backups and 100% know-I-can-restore to the same point I'm at when any version of those backups was taken.  Different systems have a different number of versions - 60 - 120 days, depending on the risk factors.  Anyway, I'm a fan and have looked at a number of other backup tools over the years.  Hopefully, some proponents of those other tools will reply so you get a nice compare/contrast view. The best backup tool for me isn't necessarily the best tool for your needs.  After all, ddrescue might be the best tool for your needs. I dunno.

BTW, questions very similar to this is asked a few times weekly here. There are many threads with good options and answers over the last 4 yrs. Be certain to check those out too.

---

