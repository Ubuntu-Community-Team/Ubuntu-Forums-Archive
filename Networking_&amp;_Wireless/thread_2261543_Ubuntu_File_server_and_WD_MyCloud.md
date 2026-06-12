---
title: "Ubuntu File server and WD MyCloud"
date: 2015-01-19
forum: Networking &amp; Wireless
---

### Post by terence8888 on 2015-01-19
Hello,

I need some help in getting my Ubuntu File server to work with WD Mycloud.  I've been running the Ubuntu server for a number of years.  Basically it's the file server for my Windows PC (using Samba).  I recently bought a WD Mycloud for backing up the files on the Ubuntu.  I looked up various threads and managed to get the Ubuntu and Mycloud talking.  The Ubuntu mounts the WD on /mnt/MyCloud.  But when I do (as user not root) rsync -av --delete /home/ /mnt/MyCloud, Ubuntu complains that I cannot chgrp etc. (prob because those are files do not belong to the user as /home houses other users' files too) , it runs but grinds to a halt eventually and I have to <ctrl>c to stop it.  

The plan is to have a cronjob run by the user eventually.  

Any help is highly appreciated!

---

