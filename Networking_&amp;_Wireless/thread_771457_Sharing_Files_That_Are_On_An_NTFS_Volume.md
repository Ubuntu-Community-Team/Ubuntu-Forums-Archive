---
title: "Sharing Files That Are On An NTFS Volume"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by Brando569 on 2008-04-27
I'm having a hell of a time trying to share files that are on an NTFS volume, samba keeps saying that the share doesnt exist and NFS says that the directory that im trying to share doesnt support NFS export. can someone please help me with this?

---

### Post by jetsam on 2008-04-27
Have a look at the second post in this thread:
[http://ubuntuforums.org/showthread.php?t=417785&highlight=NTFS+mount]("http://ubuntuforums.org/showthread.php?t=417785&highlight=NTFS+mount")

It details a simple change to the mount command that may make your share work better with Samba.  After that, check that you have sensible permissions for sharing the directory with 'ls -l' in the terminal.  

I think you'll have to use Samba.  I'm not positive, but it's probably just in the nature of NFS that it won't share files from an NTFS mount.

---

### Post by Brando569 on 2008-04-28
awesome thanks a lot! now I dont have to reboot into windows when I want to watch stuff in the living room via my xbox

---

