---
title: "Backing up Win machines onto Ubuntu"
date: 2015-04-10
forum: Networking &amp; Wireless
---

### Post by mick14 on 2015-04-10
Hi,

How are people backing up there windows machine to Ubuntu server.  Is there Linux software that will backup folders from windows machines to my Ubuntu files server ? 

thank you.

---

### Post by sandyd on 2015-04-10
> **mick14 said:**
> Hi,

How are people backing up there windows machine to Ubuntu server.  Is there Linux software that will backup folders from windows machines to my Ubuntu files server ? 

thank you.
There are countless options. To name a few...

Samba (Use a windows backup program to backup to the SAMBA share)
CrashPlan (Install headless Crashplan client on server and use CrashPlan on Windows to backup to the server)
[BackupPC]("https://help.ubuntu.com/community/BackupPC")

---

### Post by gordintoronto on 2015-04-11
To backup Windows, you will use Windows software, pointed to a Share on your server. Macrium Reflect is a popular choice.

---

