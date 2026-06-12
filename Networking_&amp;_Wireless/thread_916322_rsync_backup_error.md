---
title: "rsync backup error"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by pgcrockhead on 2008-09-10
For a while now I have been using rsync to backup my laptop's documents over my university network onto my Gutsy Gibbon desktop in my dorm. I have been using Putty to tunnel the rsync traffic, and it all worked pretty well... until I installed Hardy Heron on my desktop.

Now when I try to use rsync I get an error on my laptop using this command:

> rsync -var --dry-run "/cygdrive/c/Documents and Settings/Phil/My Documents/" phil@127.0.0.1::docsbackup

And the error I get is:

> rsync: read error: Software caused connection abort (113)
rsync error: error in rsync protocol data stream (code 12) at /home/lapo/packaging/tmp/rsync-2.6.9/io.c(604) [sender=2.6.9]

My rsyncd.conf file is as follows:

> [docsbackup]

        path = /home/phil/backup/mydocs
        read only = false
        comment = Tablet's Doc Backup Location
        uid = phil
        auth users = phil
        secrets file = /etc/rsyncd.secrets

I added "rsync stream tcp nowait root /usr/bin/rsync --daemon" to /etc/inetd.conf on my desktop and used "netstat -ln" to make sure rsync was listening on port 873, and it was. What am I doing wrong?

My laptop runs WinXP Tablet Edition with cygwin. Thanks in advance for any help.

---

