---
title: "partitions for ubuntu server"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by bnhrobotics on 2009-11-01
Hi All,

I am going to put ubuntu server on an old desktop with a software RAID1. I plan to use it for a webserver, SVN server and maybe a couple other things. What partitions should I have as separate paritions?

I was thinking:
swap
/
/home
/var

Any others that would be useful for a server? Thanks

---

### Post by unamanic on 2009-11-01
I have a similarly used box (although running fedora).  I've found that creating a partition and mounting it a /srv/ prartition and web server configs pointed at /srv/www survived rebuilds better than a separate /var would.  Since my box is essentially headless, I didn't bother with a separate /home.

---

### Post by bnhrobotics on 2009-11-01
So are you saying that you simply creating a /srv partition for everything that your server served? Then pointed at it with whatever programs you were running? Can that be done for SVN as well? Thanks

---

### Post by unamanic on 2009-11-01
I would imagine so, although I don't run SVN (do more git now a days, and even that is hosted a github) I recall you can initialize an SVN repository anywhere.

IU started doing the /svr thing when I tried out SuSE.  That's the way they do things and really has helped.

---

### Post by bnhrobotics on 2009-11-01
I appreciate the input. However, I would like to see if there are any other opinions or if this is what everyone does. Thanks

---

### Post by bnhrobotics on 2009-11-02
If I were to upgrade the server, or my desktop for that matter (with a separate /home) do I have to back up the partition before reinstalling, or does the installer know not to touch some of the partitions that are already there?

---

### Post by LewRockwell on 2009-11-02
saw your thread

thought of these

[http://ubuntuforums.org/showthread.php?t=1274259](http://ubuntuforums.org/showthread.php?t=1274259)

might help

might just be good reference

.

---

### Post by unamanic on 2009-11-02
You simply specify partitions manually, and give the partition a mount point without telling it to format it.

---

