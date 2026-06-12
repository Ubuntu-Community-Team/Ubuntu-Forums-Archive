---
title: "rsync taking ages"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Twizzle on 2009-04-22
I have been playing around with rsync to make daily backups from my Ubuntu PC to my Ubuntu server. Both are using the ext3 file system and the server is permenantly mounted to my /home directory.

My documents directory is around 95Mb and my photos directory is around 5.9Gb and the command I have been using to run the back up is:

rsync -r --delete-after -v /home/john/Documents /home/john/SERVER/Backup/Documents

and the same for the photos with the obvious change in location.

It seems to take AGES to run the script. I accept that the first time rsync runs, it copies all the photos over but after that I thought it just checked they were the same and left it at that and I should see a massive increase in speed.

Two things have come to mind as being possible problems:

1. If I select properties of the mounted /SERVER location, it says the file system is cifs and not ext3 - is this causing an issue when rsync runs?

2. I have noticed that the photo folder on the server is not the same size as on the PC. Looking into this is appeared that I had some photos on the PC in the same folder with the same name but in different cases but when synced, these were being ignored. Ie. ABC123.jpg and abc123.jpg on the PC but only abc123.jpg on the server. Have I missed something in the command line to maintain the case etc of each file?

I would really appreciate anyone who knows a bit more about rsync than me to suggest where I am going wrong or if I am expecting too much (that probably includes everyone by the way!)

Thanks

---

### Post by freak42 on 2009-04-23
use the -a flag (archive) (it also includes the -r flag), it should not update files that have not changed (either by change date or file size (not sure wich is default).

I use rsync -avz ....

a for archive
v for verbose
z for compressed-transfer (if possible)

also there are a ton of rsync tutorials out there
and the above options amongst others are explained in the man pages
man rsync

hth

---

### Post by KyleBrandt on 2009-04-23
For increased verbosity add multiple v switches.  Two is probably enough, but three will give more information.

```
rsync -avv bar/ foo:~/bar/ 
```

---

