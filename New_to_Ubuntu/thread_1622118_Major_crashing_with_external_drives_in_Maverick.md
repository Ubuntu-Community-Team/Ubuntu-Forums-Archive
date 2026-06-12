---
title: "Major crashing with external drives in Maverick"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Orographic on 2010-11-15
Hi there,

I am at my wits end with this problem after hours of trial and error today.

I've been using my NTFS formatted external drives to copy files from my wife's XP computer for years, then I copy these files to my Ubuntu PC then on to other NTFS external drives. Its worked nigh on perfectly until today in Maverick.

I thought it was my older IDE external drive failing but then I just tried it on another new external drive that is working perfectly in Ubuntu and Windows and the exact same problem occured but it has occured at a different time in the copying process each time today. The copying just stops then this:

This is the error that Linux (Maverick) gives when trying to copy over my wife's documents via the NTFS external drives that I have done for years with no problems:

Error while copying b003.au (file name varies)

There was an error in copying the file into home/...

Then when I select skip file or cancel etc, it shuts down the process but then I can't shutdown Maverick, it will just hang on shutdown, giving me the dots but nothing else. Its a serious issue and I have tried for many hours to resolve it without success. All of my backups on this new drive could well now be corrupt as I can't shut down Maverick properly.

This is happening via two external drives and I reformatted one of them today as well (NTFS) just in case of corruption but the same problem occurs. 

Help! :(

---

### Post by Hippytaff on 2010-11-15
Any usueful info in the logs
```

cd /var/log/

```
also
```

dmesg | tail

```
might provide some info :-)

---

### Post by Orographic on 2010-11-18
Sorry, I re-imaged my Maverick install with clonezilla so no logs available now...:(

Seems like it was a problem with my wife's XP files but they have always copied fine until now.

---

