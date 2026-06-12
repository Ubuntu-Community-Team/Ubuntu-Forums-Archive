---
title: "Error copying file into smb: Permission denied"
date: 2017-08-28
forum: Networking &amp; Wireless
---

### Post by HDTimeshifter on 2017-08-28
I got the above error trying to copy a file from my main desktop 16.0.4 PC to my file server 16.0.4 desktop. I first got this error a couple of days ago and when I tried to open the file from my server, it would open as read-only. I checked another 16.0.4 desktop PC to see if I had left the file open there (and locked), but it was not and also would only open as read-only from that computer. I was only able to resolve the problem by turning off the local network share of the folder on the server and re-share it.

However, tonight, when I got this error, I tried turning off an back on the network share from the file server, but it did not solve the problem. I also tried rebooting the file server as well as my main PC, but I am still unable to (backup) copy the file to the file server. I've been doing this backup operation for years now since at least Ubuntu 12.x only recently got this error. Is there a bug in the latest Ubuntu update or what?

---

### Post by TheFu on 2017-08-28
Did you check the log files?  Always start there.  Under samba, every connection creates it's own log --> /var/log/samba/ ... 

NFS is the native network file sharing method on Unix-like systems.  File permissions work exactly the same local/remote over NFS. NFS is FASTER than SMB/CIFS too.

For backups, using any network file sharing protocol is dangerous.  We've learned this from the windows guys where they have viruses that encrypt any storage found either connected or via SMB/CIFS.  Fortunately, on Unix we have better backup options that don't use network file sharing.  1 option is rdiff-backup, but there are many others.  Just setup ssh keys between the systems - it is better to "pull" the backup than to "push" it from a security standpoint.  Clients tend to be more likely hacked, so allowing the client to "push" backups would mean the client has some sort of access to the backup server. That's an attack vector.    Anyway, ask if you'd like to know more.

---

