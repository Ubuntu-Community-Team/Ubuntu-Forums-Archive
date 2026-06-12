---
title: "sbackup and dropbox - confused about permissions"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Knacker on 2009-06-22
Hi, 
I'm trying to do something that seems like it should be pretty simple, but it's not working and I can't figure out why. I want sbackup to do incremental backups of a folder (recursive) and put the backups in my dropbox folder. This part, I've figured out and it's working...except:

The problem is that when i check the web-interface for my dropbox account (i.e. the web-version of the folder that has been synced with the folder that my backups are dumped into), the folders on there that should contain the backups on my computer are all there, but they appear as "Empty." Obviously this is *a bit* of an issue for my backup solution.

I'm pretty sure that the problem has to do with the fact that sbackup is creating files that you need to be root to read/write. I've searched and searched. I just want something exactly like sbackup that will just let *anyone* (especially dropbox) read/write/own the backups that it makes.

I'm sure others have run into this...but the fact that I can't find any answer anywhere is making my head hurt. 

Doesn't need to be with sbackup...as long as it's simple and just works. Anyone?

---

### Post by mike555 on 2009-06-22
I haven't had very good luck with sbackup , I now use "Back in Time" .......  [http://backintime.le-web.org/](http://backintime.le-web.org/)   , it works great and doesn't compress the backup, and only backs up changes, not full backups that fill the backup partition ...........

---

### Post by Knacker on 2009-06-23
looks good. will give it a try. thanks a lot!

---

### Post by gtr225 on 2009-09-14
does backintime save backups as root?

---

### Post by dik23 on 2009-09-30
I have been having a similar problem with Wuala.

SBackup 0.10.5 saves backups with permission root:root

If you install ver 0.10.4 it saves as root:admin

This means that as long as you've got admin rights on your machine you (and therefore dropbox) will be able to read the contents of the files SBackup produces

Hope this helps

---

