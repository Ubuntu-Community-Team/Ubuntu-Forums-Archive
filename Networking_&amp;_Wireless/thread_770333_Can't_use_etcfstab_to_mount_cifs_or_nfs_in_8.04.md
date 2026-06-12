---
title: "Can't use /etc/fstab to mount cifs or nfs in 8.04"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by owen_pg on 2008-04-27
Is using /etc/fstab for mounting remote filesystems deprecated in 8.04?

I did a fresh install for kubuntu 8.04 amd64 desktop installed.  All went well until adding nfs-common package and adding nfs mount details to /etc/fstab.  The system now won't boot correctly - errors at boot-time, see here for details:
[https://bugs.launchpad.net/ubuntu/+bug/213444](https://bugs.launchpad.net/ubuntu/+bug/213444)

I removed the nfs-common package and appropriate /etc/fstab entries and changed the mounts in /etc/fstab to mount the same server share points under the cifs protocol - it serves them as both NFS and CIFS.  I get to see the data on the remote file system but upon reboot, there is an error after "running local.rc scripts" - no details are given and the PC never boots to KDE.

Is there a new way to mount network file systems rather than /etc/fstab with 8.04 ?

---

### Post by cmost on 2008-06-12
My research indicates that this problem has occurred due to an update to packages in Debian Testing.  I have tried to implement several "workarounds", including recompiling nfs-common with patches, but so far without success.  I'm still working on it.  There is some information on how to mount your shares with CIFS without the error you've reported.  Do a Google search and you'll probably find the same pages I did.  Also, I've had some success using smb4k, even in Gnome as a temporary fix.  As a side note, the fact that nobody has replied to this very important problem is yet more evidence that Ubuntu developers don't really care about their distribution once it goes gold.  Further, the Ubuntu community, comprised mostly of newbies entranced by Compiz-Fusion, don't know what you're talking about when you say such strange things like "NFS" or "CIFS".  For an LTS release aimed at corporate users to have this problem with networking is a disgrace.  While I'm sure it will be fixed in Debian eventually I have my doubts that Ubuntu will get to it, since they're too busy adding flash and glamor to "Ibex".  Good luck!

---

