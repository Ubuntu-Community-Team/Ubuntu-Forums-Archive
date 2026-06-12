---
title: "Backing up files that are in use?"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by raccoonone on 2009-05-20
I'm trying to setup a backup system for my computer, and I read several guides that suggested using tar. However when I use it I often get warnings saying "file changed as we read it," how do I get around this problem? I want to be able to still use my computer while the backup is running.

---

### Post by glennric on 2009-05-20
You can usually ignore those messages.  Tar gives a lot of warning messages that are not serious.  Usually those are log files being written to, or cached files.  I use tar to backup my entire system once a week.  I always get a few of those messages, but I have restored those backups and they work perfectly with no lost data.

---

### Post by raccoonone on 2009-05-20
Thanks, I may just ignore them. Would using LVM to make a snapshot solve my problem?

---

### Post by glennric on 2009-05-20
I don't know.  I have have never used LVM.

---

