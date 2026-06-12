---
title: "Looking for Shared Files"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by Sugi on 2008-01-30
I am trying to access shared files in my school for class projects and teachers.  I am trying to do this without setting up any Network drivers through Samba or the NFS that come with Ubuntu.  I think it's possible to see those files being shared over the network without myself sharing files.

My question is, Can I see files without Samba or NSF?  Can I copy them over as well?  If not, can I get away with using NFS instead of Samba?  I have no needs at this moment to host files over a network.

Thank you,
Sugi

---

### Post by mpokrywka on 2008-01-30
It is possible to browse and copy files in "Microsoft Network" (smb) using standard ubuntu file manager, just type file address like "smb://ip.of.comp.uter/"  - this works under konqueror - I use kubuntu, but I'm sure gnome supports this convention too, there should be something like "Remote places" or something too, to browse smb network
> I am trying to access shared files in my school for class projects and teachers
The real question is: do you want to access files that are on school network while you are on different network (home/other work/isp)?
Or you are school teacher/admin and want to make those files accessible from "outside"?
Solution could be apache http server working on samba file server - files could be accessed from internal school network using samba("network neighbourhood") and from outside(internet) they could be downloaded with browser...

---

### Post by Sugi on 2008-02-05
I am unsure if I understood you corrently.

I connect to one of many wireless networks in my school building and get internet that way.  All networks within the school (wired or wireless) has files being shared over them.  I am connecting to the school wireless and I know those files are being shared, but I am unsure on how to see them.  Do I just open up a folder manager and type smb:// then it shows me all the shared files in my schools network.  Can I do that?

---

### Post by mpokrywka on 2008-02-06
> **Sugi said:**
> Do I just open up a folder manager and type smb:// then it shows me all the shared files in my schools network.  Can I do that?
That should work, only use address "smb:/" or "smb:///" (one or three slashes) so that you will be able to see all windows network workgroups...

---

### Post by Sugi on 2008-02-06
ha, i was trying smb:// not "/" or "///"  i was close.  Thanks for the help.  I'll report back with the outcome. :)

Sugi

---

