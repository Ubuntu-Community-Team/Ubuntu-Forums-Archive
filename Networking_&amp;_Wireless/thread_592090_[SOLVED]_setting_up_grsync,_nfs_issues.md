---
title: "[SOLVED] setting up grsync, nfs issues"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by a_posse_ad_esse on 2007-10-26
Here is my scenario:

My network consists of two laptops (which are used by my wife and I for schoolwork and rove on various networks accordingly) and a workstation.  The workstation will not be a problem, as the IP can just be assigned, but the laptops, to my knowledge, cannot have assigned IPs as every network has a different range.

The plan is to have an nfs mounting system in place as follows:
grsync-laptop /home/user folder <-> /mnt/sync <-> grsync-server  <server>:/mnt/sync/home <-> /home/user <-> <workstation>/mnt/sync
grsync-workstation /mnt/sync <-> /home/user

I realize that this is complex, but it is the only way I see of keeping a) the appropriate files backed up on the server without having the /home folders mounted directly to the server b) live updates to laptop/worstation when files are modified.  If this can be simplified, let me know, as complexity breeds problems.

The current plan is to use nfs to have the mounts in place, as it is faster than samba by my experience and security is not currently an issue.  Switching over to samba would be easy enough as the principles are the same...  However, since the laptops cannot have an assigned IP, I have to rely on hostnames in fstab.

Here is what I have for the server:

```

laptop:/sync/home /sync/home/user nfs user,auto,rw 0 0

```

However, when I try to mount...

```

sudo mount /sync/home/user
mount.nfs: can't get address for laptop

```

This had me puzzled for a little while, but when I ran nslookup, I got

```

Server:         192.168.2.1
Address:       192.168.2.1#53

Non-authoritative answer:
Name:   laptop
Address: 192.168.2.3

```

This is wrong, as ifconfig on the laptop says that the proper address is 192.168.2.8 (for whatever reason).

I'm stuck.  Any suggestions?  Thanks.

---

### Post by a_posse_ad_esse on 2007-10-30
I have abandonded grsync, as it does not seem to have anything allowing for cron jobs.  I want my backups to be automatic, so I will just use rsync.  The problem remains the same however.

---

### Post by a_posse_ad_esse on 2008-01-16
I have started working on a [solution]("http://ubuntuforums.org/showthread.php?t=655969").  Any feedback would be appreciated.  Thank you.

---

