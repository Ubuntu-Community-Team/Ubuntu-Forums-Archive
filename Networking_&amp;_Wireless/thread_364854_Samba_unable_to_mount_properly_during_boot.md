---
title: "Samba unable to mount properly during boot"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by itsthescottdog on 2007-02-18
I'm running Xubuntu 6.10 with all of the latest updates and recently I haven't been able to get my network shares to mount properly during startup on my iBook. Every time I try to "ls /media/share" it gives me an I/O error. If I "umount /media/share/" then "mount /media/share" I can access the network share just fine.

Here's the line from my fstab file
//192.168.0.103/share          /media/share         smbfs          credentials=/root/.smbcredentials,dmask=777,fmask=777    0   0

Samba will also give me a "retry" error during shutdown if I didn't remount the shares.

I didn't have this problem before I came home from college... so maybe it has something to do with my home wireless network?

---

### Post by n00bish on 2007-02-18
I think your problem may lie in that you're on wireless.. That doesn't connect on startup, afaik.  You'll need to be plugged in physically to be able to mount that share on boot..

---

### Post by itsthescottdog on 2007-02-18
Thanks, I guess I did have problems once while I was at college - the one day I didn't boot up my iBook in my dorm room on the ethernet.

---

