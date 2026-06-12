---
title: "Tar fails with sshfs mounted file system"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by mnb on 2008-03-12
Hi all, this one has me stumped and I'd appreciate your thoughts.  I'm trying to backup my fileserver via a script on my laptop.

I mounted the fileserver's file system on my laptop with the following:

"sudo sshfs mnb@capella:/ /mnt/capella -o idmap=user -o allow_other -o uid=1000 -o gid=1000"

This works great, and I can browse, read and write the mounted system from my laptop.  BUT when I attempt to backup the mounted file system with Tar, the job apparently fails and always creates a 45 byte file for the resulting file.  I assume this is some sort of header.

If I point the same tar job to some local target on the laptops file system - the job runs fine.... but any target on the sshfs mounted system always creates a 45 byte file and stops.  And it doesn't matter whether I run the tar job as the userid on the mount statement or root either....   any thoughts?

THanks - Michael

---

### Post by mnb on 2008-03-12
Oh... and my laptop system is Fiesty and the fileserver is Server 6.06 Edgy.

---

