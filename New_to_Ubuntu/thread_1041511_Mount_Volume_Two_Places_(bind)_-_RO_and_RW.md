---
title: "Mount Volume Two Places (bind) - RO and RW ?"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by thornomad on 2009-01-16
Hi -

Is there a way to mount the same volume two places: one read-only and one read-write?

I want to mount my backup folder somewhere read-write (so root can backup all user's folders to it); and I want to mount it in the user file-space as read-only (obviously, so they don't delete or mess with the backups).

I played with mount --bind and can get it to mount twice, no problem, but the read/write settings mirror each other on both mount points ... 

Is this even possible ?  Or would I have to use an NFS export or something like that ?

Thanks,
Damon

---

