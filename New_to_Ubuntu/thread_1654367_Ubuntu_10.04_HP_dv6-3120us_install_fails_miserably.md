---
title: "Ubuntu 10.04 HP dv6-3120us install fails miserably"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by alfu on 2010-12-28
Booted from a Ubuntu 10.04 live CD.  Looking at the Windoze 7 file directories, we could see no files on the existing partitions (just an error dialog box), and no WiFi.  

In resizing the largest (~450Gig) partition with GPartEd, as soon as the new size was entered, GPartEd folded with a user login dialog box, and the only option was to power down manually.  

Then booted with Ubuntu 9.10 live install CD.  Still no WiFi.  Contents of the Windoze directories listed, however.  

We could re-size with GPartEd, but an error message let us know that Windoze 7 had already sucked up all four of the primary partitions, so we would have had to migrate data off the biggest one to repartition it into some extended partitions.  These partitions are: one of about 200MB for language definitions labelled SYSTEM (!?!), one unlabelled for the actual system & all user files, one ~16GB for recovery and a small one for tools.
 
Since there was no WiFi at that point anyway, we re-booted into Windoze 7, and got the black screen of death.  Pet rock. Unfun.

---

