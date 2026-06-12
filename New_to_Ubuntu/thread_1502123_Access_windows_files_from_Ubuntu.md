---
title: "Access windows files from Ubuntu"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by Stanich on 2010-06-05
Ok i have a problem. I installed ubuntu through windows (me fool) so now i have them both on same partition. And i want to access files i have had on windows via Ubuntu. I would really appreciate any help.

P.S.: Also i have some unfinished downloads on windows (via micro torrent) can i finish them anyhow?

EDIT: Also I am very noobish at ubuntu, so i would like some extraordinary user friendly instructions.

---

### Post by Achilles124 on 2010-06-05
I guess you want to save the files you have on windows. The important ones. Easy. Use a Live cd to access your harddisk and then save the files on a USB stick.

---

### Post by 3rdalbum on 2010-06-05
> **Stanich said:**
> Ok i have a problem. I installed ubuntu through windows (me fool) so now i have them both on same partition. And i want to access files i have had on windows via Ubuntu. I would really appreciate any help.

P.S.: Also i have some unfinished downloads on windows (via micro torrent) can i finish them anyhow?



First problem:

Since you've used Wubi, assuming that Ubuntu is sitting on the same partition as Windows, you can just go to /host to access your files.

Go to the Places menu and come down to Computer. Then double-click on Filesystem, and then the 'host' folder. Presto!

Second problem: I don't think so, unless that torrent software also works on Linux. If it does, then you may be able to copy the preferences file across to Linux, put it into the place that the program expects it to be, and change the entries for the 'current torrents' to point to the new file paths on Linux (because Linux file paths are completely different to what you'd find on Windows).

Probably a bit too advanced for you, and I haven't heard of Micro Torrent before so it's probably not on Linux. Just finish them on Windows and start all new ones on Linux :-)

---

### Post by Stanich on 2010-06-05
> **3rdalbum said:**
> First problem:

Since you've used Wubi, assuming that Ubuntu is sitting on the same partition as Windows, you can just go to /host to access your files.

Go to the Places menu and come down to Computer. Then double-click on Filesystem, and then the 'host' folder. Presto!

Second problem: I don't think so, unless that torrent software also works on Linux. If it does, then you may be able to copy the preferences file across to Linux, put it into the place that the program expects it to be, and change the entries for the 'current torrents' to point to the new file paths on Linux (because Linux file paths are completely different to what you'd find on Windows).

Probably a bit too advanced for you, and I haven't heard of Micro Torrent before so it's probably not on Linux. Just finish them on Windows and start all new ones on Linux :-)
Thank you for help and your time.

I also suceeded in starting downloading items i haven't finished on windows. :P

---

