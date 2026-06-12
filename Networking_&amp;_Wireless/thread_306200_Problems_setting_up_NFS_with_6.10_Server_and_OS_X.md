---
title: "Problems setting up NFS with 6.10 Server and OS X"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by SiR GadaBout on 2006-11-24
Hi,

I'm struggling to have OS X Panther mount an NFS share served on an Ubuntu 6.10 Server box.

The ethernet port on both computers work - I've SSH'd over them.  The cable works.  I created a user account on Ubuntu with the same uid and username as the user I'll be accessing from on OS X.  Ditto with the group account.  I've even given the Ubuntu user account the same password as I use on OS X for the respective user.  I've exported the appropriate directory in the /etc/exports file, with the correct IP address and access settings.  NFS Server is running.

The problem is always a username/password error on the client end.

The only things I can think to mention are that the shared directory was created at root, and the uid and gid are 501 - which is the reserved segment, right?

Is it one of these last two facts that explains my problems?  Please tell me especially that it's definitely not the last one - the uid/gid being in the reserved space.  The last thing I want to do is start mucking about with my uid/gid settings on my Mac - if it ain't broke…

Please help.  Also, if you can help me with my other queries too I'd be grateful.  There seems to be very little documentation for Edgy Eft at the mo'…

SiR G.

---

