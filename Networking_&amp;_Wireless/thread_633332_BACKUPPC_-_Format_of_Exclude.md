---
title: "BACKUPPC - Format of Exclude"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by mcgerard on 2007-12-06
I am new to Linux and Ubuntu but so far have installed 7.10 on a spare box and backuppc on top of that. Eventually I hope it will do a sever role and backup my Windows machines. Backuppc is running and starts a backup but fails because of lack of disk space, the problem being large video files which I don't actually want to backup.

I am using SMB and I have the specified the Windows share as 'My Data (E)' which is what it is shared as under Windows. I must have got that right as it starts to backup that share. Within 'My Data (E)' is a folder of video files named 'DigiTV Recordings'. I have added an exclude which I have specified as 'My Data (E)/DigiTV Recordings/*'  That must be wrong as it proceeds to backup that folder and fails because of lack of space. What is wrong with my Exclude format? Have I got the slashes right? I added the * at the end in line with backuppc config file advice to catch sub-folders. Is that right?

---

### Post by mcgerard on 2007-12-16
I got an answer to this through the Backuppc Users Mailing List.  I should not have included the share name again within the exclude statement. So in my case above the exclude should be specified as '\DigiTV Recordins\*' My backups now run to completion.

---

