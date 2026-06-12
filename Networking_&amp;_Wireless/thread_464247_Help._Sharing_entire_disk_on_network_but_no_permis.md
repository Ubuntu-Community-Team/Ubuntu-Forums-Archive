---
title: "Help. Sharing entire disk on network but no permissions to even create directory"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by newuser19 on 2007-06-04
Hi I'm new. version 7.04.

I have everything installed. Have 2 physical hard disks. 1st for Ubuntu and 2nd for file storage. I don't know how to share that 2nd hard disk. It seems that I have insufficient rights to do anything with it. All I want is to share that entire disk so MS Windows users can read/write on it. It's for file storage only. I can't even create a directory in that 2nd harddisk. In the GUI, that option is 'de-highlighted.'

Help would be appreciated.

---

### Post by 99bluefoxx on 2007-12-01
search the forums for tutorials on "chown" and "chmod" as well as "su" and "sudo" tutorials
best i can offer you
good luck

---

### Post by victorbrca on 2007-12-01
There's a bit more that needs t be done so you can get your disk shared, but first I would find out why you can't create folders on it. 

Is this a new install? Where did you mount the disk? run the following code inside the disk in case is still fairly empty (only if it's fairly empty), and post the result here:

```
ls -lR
```


Vic.

---

### Post by 99bluefoxx on 2007-12-02
at least i was abel to resurect this thread s a more knowlagable person could give a response, i suppose
im wondering
how well does 7.04 support SATA?
i am considering buying a second harddrive to backup to to do a reinstall as a few things are "broken", and am planning to also install wondiws

---

