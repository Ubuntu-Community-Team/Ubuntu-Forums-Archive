---
title: "[SOLVED] BackupPC &amp;amp; Samba Questions"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by rkulp on 2008-05-11
First, if this is posted in the incorrect area, please forgive this newbie. I have set up BackupPC in Hardy and also have tried to implement GSambad. I have some questions.

1. I can ping the Windows XP computer, both by IP and alias, in a terminal session. However, when trying to do a backup I get an error that the ping failed. Any ideas why?

2. I have had added the Windows computers on my network in the hosts section. They appear to resolve properly, if pinging by the alias is any indication. However, I can't add them to GSambad machines. The error is that the "computer does not exist." Where do I add the computer so it exists?

Additional note:  The Windows computers reside on a Windows peer-to-peer network, MSHOME. They receive their IP addresses from the router so I changed the Ubuntu computer to have the same address as assigned by the router, 192.168.0.8, rather than in the 127.x.x.x addresses. However, I have left the localhost as 127.0.0.1. This was the only way I found to resolve all the networked computers. I expect there is a better way.

Also, I expect there will be additional problems appearing when these are resolved. I would especially appreciate a BackupPC expert to respond.

Thanks in advance for your generous support.

---

### Post by rkulp on 2008-05-11
> **rkulp said:**
> 

1. I can ping the Windows XP computer, both by IP and alias, in a terminal session. However, when trying to do a backup I get an error that the ping failed. Any ideas why?

Additional note:  The Windows computers reside on a Windows peer-to-peer network, MSHOME. They receive their IP addresses from the router so I changed the Ubuntu computer to have the same address as assigned by the router, 192.168.0.8, rather than in the 127.x.x.x addresses. However, I have left the localhost as 127.0.0.1. This was the only way I found to resolve all the networked computers. I expect there is a better way.

Also, I expect there will be additional problems appearing when these are resolved. I would especially appreciate a BackupPC expert to respond.

Thanks in advance for your generous support.

Upon looking at the log file again, I see that the ping has worked on the latest attempts so this is OK. The problem now is the inability of backuppc (BackupPCUser) to open the log file XferLog in the location where the backups are stored: /storage/backuppc/pc/dc6mqf61. I have tried increasing permissions but no luck yet.

---

### Post by rkulp on 2008-05-12
> **rkulp said:**
>  The problem now is the inability of backuppc (BackupPCUser) to open the log file XferLog in the location where the backups are stored: /storage/backuppc/pc/dc6mqf61. I have tried increasing permissions but no luck yet.

The problem was ownership of the folder. Changing it from root to backuppc solved it.

---

