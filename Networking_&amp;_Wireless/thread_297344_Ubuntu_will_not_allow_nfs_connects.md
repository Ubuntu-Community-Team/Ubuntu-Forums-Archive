---
title: "Ubuntu will not allow nfs connects"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by larryalk on 2006-11-11
I am not able to access Ubuntu over nfs from another computer, probably because the nfs daemons do not start on bootup.

I made this script to get the daemons started but Ubuntu still won't serve nfs.  What can I do?

This is my little script:
root@kinda bin # cat nfsstart.kinda

# lba: nfsstart.kinda - Start the nfs daemons
# The nfs daemons need to be started since they do not start in default runlevel 2.

# nfs-common starts nfs and statd
/etc/init.d/nfs-common restart

# nfs-kernel-server starts mountd and nfsd
/etc/init.d/nfs-kernel-server restart

# start portmap
/sbin/portmap -v
 exit

Larryalk

---

