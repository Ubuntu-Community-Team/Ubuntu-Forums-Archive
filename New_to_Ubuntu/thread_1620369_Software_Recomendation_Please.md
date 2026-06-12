---
title: "Software Recomendation Please"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-11-13
I just switched from windows to ubuntu and i love it.  I am looking for software to back up my partition.  Does anyone have any ideas for an ubuntu disk imaging software?  If possible i would like one that makes a boot disk. Thanks

---

### Post by kroq-gar78 on 2010-11-13
do you want ot just back up your ubuntu partition? all you have to do is create a giant tar (archive) file for your root ("/") folder and do everythnig from there.

here is a page you can do this from. remember to add the "--exclude /media" option (w/o quotes) so that you don't backup anything else: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

This also describes a way that can be done using a live cd. this actually creates an image and not just a zip archive at the bottom of the page: []("http://ubuntuforums.org/showthread.php?t=35087")[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

hop it helps.

---

### Post by jmszr on 2010-11-13
hunter99507,

Here is a link that should be of help: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) . 

I use Back-In-Time, it is a GUI for rsync that works well and is pretty simple to use: [https://launchpad.net/~bit-team/+archive/stable](https://launchpad.net/~bit-team/+archive/stable) . Here is their website: [http://backintime.le-web.org/](http://backintime.le-web.org/) .

---

### Post by sikander3786 on 2010-11-13
Clonezilla has always worked for me.

[http://clonezilla.org](http://clonezilla.org)

And as a bonus point, it also comes on a Live CD. Just like any other proprietary imaging software like Acronis Image or Norton Ghost.

---

