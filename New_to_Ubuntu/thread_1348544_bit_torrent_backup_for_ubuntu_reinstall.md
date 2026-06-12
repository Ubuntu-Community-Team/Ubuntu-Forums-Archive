---
title: "bit torrent backup for ubuntu reinstall"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-12-07
where do i go to back up bit torrent (the default bit torrent)for ubuntu? I need to reinstall ubuntu and i want my files.

---

### Post by mvalviar on 2009-12-07
> **lance bermudez said:**
> where do i go to back up bit torrent (the default bit torrent)for ubuntu? I need to reinstall ubuntu and i want my files.

back up the .transmission folder in your home folder and of course the unfinished downloaded files.

---

### Post by lovinglinux on 2009-12-07
Perhaps its time for you to consider a [separate home partition](http://www.psychocats.net/ubuntu/separatehome).

---

### Post by lance bermudez on 2009-12-09
I have a separate home partition. Also thier is no .transmission folder or file under /home/ubuntu

---

### Post by lovinglinux on 2009-12-09
> **lance bermudez said:**
> I have a separate home partition. Also thier is no .transmission folder or file under /home/ubuntu

The correct path is ~/.config/transmission

Anyway, since you have a separate home partition, why bother? Just make sure you don't format the home partition during re-install and mount it properly. Your torrents will be kept as they are.

---

