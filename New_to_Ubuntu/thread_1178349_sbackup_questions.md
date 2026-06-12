---
title: "sbackup questions"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by bmaguire on 2009-06-04
I am trying to do a restore to my Kubuntu system using Simple Backup and I have a few questions.  

First, does Simple Backup give any indication of when a restore is finished?  I get the "Restoring, this might take some time" window but since there is no thermometer I don't know what's going on.  Does the window just disappear when done? 

Second, just in case all else fails, is there a way to decompress the backups without using Simple Backup restore?  That would allow me to try just manually moving my data over to the appropriate directories.  This is a work computer and retrieving some of the data is pretty urgent.

Thanks for any help.

---

### Post by durand on 2009-06-04
I had a bit of problem restoring sbackups as well. You can do it manually by extracting the tar.gz file in the backup folder.

---

### Post by bmaguire on 2009-06-05
Thanks, Durand.  I think that's what I'll have to do.  Now the problem is that I can't get into the backup folders.  Access is being denied for some reason.  How did you get into the backups to extract the tars?

---

### Post by durand on 2009-06-05
Oh yeah, it has administrative permissions only so press Alt-F2 and type ```
gksudo nautilus
```. That opens the file manager as root. Then just find the file and extract as normal. Ask if you need more help.

---

