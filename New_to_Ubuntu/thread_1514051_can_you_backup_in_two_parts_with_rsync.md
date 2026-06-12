---
title: "can you backup in two parts with rsync?"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by lolzwut on 2010-06-20
I'm trying to backup only my home directory with rsync and I found a guide on how to do it but the problem is my /home is 9.4G so I need something that will hold 9.4G of data. I
only have a couple usb drives that are almost full and a bunch of blank CD-ROM's. So can I back up the data in a coupe different parts on different cds? If so how can I do it? Thanks!

---

### Post by mk1w86 on 2010-06-20
You might not be able to do it with rsync itself, but you could use tar and split to split the backed up directories into archives of whatever size you specify.

Have a look here, specifically archive splitting (you will need to scroll down a bit):

[https://help.ubuntu.com/community/BackupYourSystem/TAR#Backing](https://help.ubuntu.com/community/BackupYourSystem/TAR#Backing) Up

There is another guide here as well:

[http://maketecheasier.com/how-to-compress-and-split-files-in-ubuntu/2008/10/06](http://maketecheasier.com/how-to-compress-and-split-files-in-ubuntu/2008/10/06)

If you want the splitting to be automated you could always run it as a cron job. ;)

---

### Post by mapes12 on 2010-06-20
Found this:

[http://brainstorm.ubuntu.com/idea/6811/](http://brainstorm.ubuntu.com/idea/6811/)

& this:

[http://manpages.ubuntu.com/manpages/hardy/man1/cback-span.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/cback-span.1.html)

---

