---
title: "NFS shares slow to mount from Feisty"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by PsypherPunk on 2007-05-14
I recently updated Ubuntu to the latest version and have found that connections to it now occur much slower than before.

VNC, while previously taking only a moment, now hangs for several seconds before the password prompt appears. All the NFS shares thereon now mount very slowly from remote clients (with occasional RPC Timeout errors). Connections via FTP also suffer the above problem.

However, once connected the speed and performance are just fine. Does anyone have any ideas? Portmap has been installed (and is running) on both client and server.

---

### Post by travc on 2007-06-04
"Solution 2" here worked for me to fix NFS.  Apparently the scan for services stuff screws up both ssh and nfs.

[http://www.ubuntugeek.com/fix-for-ssh-slow-to-ask-for-password-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/fix-for-ssh-slow-to-ask-for-password-in-ubuntu-feisty-fawn.html)

---

### Post by pstracha on 2007-07-12
I had a similar problem with the NFS mounting speeds, but after making a couple of changes my mounting speeds are much faster. You can see what I did below, I made both changes at once so it may only be one of the two changes that improved my mounting speeds ... probably the second.

1. On the server side I changed the subnet entries in /etc/exports from masks to mask bits, ie:

instead of ...
```
192.168.1.0/255.255.255.192(blah blah ...)
```

I made it ...
```
192.168.1.0/26(blah blah ...)
```

2. Installed nfs-common & portmap on the client

```
sudo apt-get install nfs-common portmap
```

---

