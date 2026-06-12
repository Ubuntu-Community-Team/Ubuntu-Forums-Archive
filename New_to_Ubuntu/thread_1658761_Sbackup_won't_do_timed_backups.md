---
title: "Sbackup won't do timed backups"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by bharesc on 2011-01-03
I am backing up to a NAS and have set the backup destination as, "smb://nas-5e-2d-b3.local/backup" and the time as hourly at 30. The system doesn't perform the timed backup. If I press backup now then I get the message that a backup is being performed and the incremental backup is saved in the NAS folder.
Any help would be appreciated.

---

### Post by Wtower on 2011-01-03
Can you check if there is a script named sbackup in /etc/cron.d ? Can you check the /var/log/syslog file for the appropriate cron entry, so that at least we know it executes? Can you check the log file /var/log/sbackup/sbackup.log ?

---

### Post by bharesc on 2011-01-03
Thanks for your reply.
1. There  is a script named sbackup on /etc/cron.d
2. There is no /syslog in /var/log
3. There is no /sbackup in /var/log
I'm looking for these files in "File System"

---

### Post by Wtower on 2011-01-03
Apparently you're not using the console so you can reach syslog in menu System, Administration, log files. The reason you cannot see the files is that only root has got the appropriate permissions.

Anyway, I would think of at least a dozen reasons why it doesn't run. For a start, could you paste the contents of /etc/cron.d/sbackup please.

---

### Post by bharesc on 2011-01-03
Here is the content of /etc/cron.d/sbackup
30 * * * *    root    if [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;
I'll look into the other files.

---

### Post by bharesc on 2011-01-03
This was in /var/log/syslog
Jan  3 16:30:01 ubuntu CRON[26314]: (root) CMD (if [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;)

There was no /sbackup in the /var/log/ file

---

### Post by Wtower on 2011-01-04
Is there a file named sbackupd in /usr/sbin?

---

### Post by bharesc on 2011-01-04
Yes, there is a file called sbackupd in /usr/sbin.

---

### Post by Wtower on 2011-01-05
Is there a file sbackup.conf in /etc ? Can you paste the contents here please.

---

### Post by bharesc on 2011-01-05
Yes, heres the listing: -

[exclude]
regex = \.mp3,\.avi,\.mpeg,\.mkv,\.ogg,\.iso,/home/[^/]+?/\.thumbnails/,/home/[^/]+?/\.Trash,/home/[^/]+?/\..+/[cC]ache,/home/[^/]+?/\.gvfs/
maxsize = 10485760

[places]
prefix = /usr

[dirconfig]
/var/cache/ = 0
/var/spool/ = 0
/media/ = 0
/var/tmp/ = 0
/home/ = 1

[general]
stop_if_no_target = 0
target = smb://nas-5e-2d-b3.local/backup
format = 1
purge = log
maxincrement = 7
lockfile = /var/lock/sbackup.lock

---

### Post by Wtower on 2011-01-06
I can see there are some sections missing comparing to a typical conf file, but before I get into that, a thought that just came to me. 

I have no experience with these samba paths of the form smb://, and I am wondering whether this is something that you mount or anyway assign as a user, or even samba creates it for you when you login, or is it something created from the samba service at bootup. Because you see, you confirm that the sbackup runs perfectly well as a user but not as a cron job, and that particular cron job is executed as root and therefore we don't know if root sees a smb:// path like that.

So what I would strongly suggest is that you avoid this and instead mount whatever is being pointed at with a standard mount command. This read shall help:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

You then can place the mount command in the /etc/cron.d/sbackup file exactly between the word root and the word if together with a semicolon.

I can't actually help more with mounting because I never needed to mount a windows share in Linux so far as all my servers have been Linux based. If you can provide me with a mount command I can tell you exactly how the cron file should look like.

---

