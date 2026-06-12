---
title: "NFS Issue Gutsy"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by yahooadam on 2008-03-24
I just upgraded to Gutsy from Feisty

I had an nfs share that was mounted by fstab
However, since the gutsy upgrade, at boot the nfs share wouldn't mount (with a message like)
NFS Share Mounting   [FAIL]
However, when i was at the desktop, the share was there and mounted

after trying to work out the issue, i found that my interfaces file has been edited, so i now had
```
auto eth0
#iface eth0 inet dhcp
```
Because of this, eth0 wasn't up at boot, and this meant that nfs is trying to mount before any interface is up

I'm not really sure what to post as a bug report for this, but am writing down the issue in an attempt to help others in the future
I'm not even sure how fixable this is (Or maybe its just an issue with my setup?) , perhaps a "fstab" that is run after networking is brought up

---

### Post by Eiríkr on 2008-03-24
Try simply incommenting the line in your interfaces file (remove the initial number symbol **#** and save).  

FWIW, after several distros and many years, I have found that upgrades to existing installations ***always*** produce weird behaviour.  Since figuring this out (most recently confirmed when upgrading from Eft to Feisty), I almost always back up, wipe, and install on a fresh partition.  

Cheers,

Eiríkr

---

