---
title: "Updates screwed all my network shares"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by RawMustard on 2006-07-20
I can't access any samba shares across the network anymore.  I get this error.

mount error 12 = Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

I haven't changed a thing, these fstab entries have been working for over 3 months.  Oh and I have tons of memory, 4 gig!

Any ideas how I might go about solving this problem?

This is one entry in my fstab.

//computer/Share        /home/username/computer/share    cifs  exec,credentials=/root/cifcred,uid=username

And I can't even access shares via nautilus connect to server, it does nothing :(

Fixed it! It was my router playing up.  You'd think you'd get some better error than can't allocate memory though, how's one suppose to know their network is playing up with stupid errors like that? ](*,)

---

