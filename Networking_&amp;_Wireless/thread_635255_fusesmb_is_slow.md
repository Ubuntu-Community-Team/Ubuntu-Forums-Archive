---
title: "fusesmb is slow"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by foresto on 2007-12-08
Has anyone else noticed that copying a file to an smb server takes about 3 times as long with fusesmb as it does with mount.cifs or smbclient?  Some example timings, copying a 358 meg file from
my workstation to my (somewhat slow) Linksys NSLU2 file server:

using mount -t cifs:
real    1m18.734s
user    0m0.008s
sys     0m1.060s

using fusesmb:
real    3m40.452s
user    0m0.096s
sys     0m1.640s

Using smbclient takes just a few seconds more than mount.cifs; still much faster than fusesmb.  I get similar results with a 5 gig file: around 15 minutes using mount.cifs, or 45 minutes using fusesmb.  I would have explained this by pointing to linux filesystem buffering, but that doesn't account for smbclient being nearly as fast as mount.cifs.  As far as I can tell, fusesmb is just plain slow.  (Which is really too bad, because I love the convenience of it.)

---

### Post by jetsam on 2007-12-18
I get about two to two-and-a-half times the performance with cifs mounts as with fusesmb.  Copying a 45 megabyte file to a windows xp based share:

mounted with cifs:
real    0m5.114s
user    0m0.000s
sys     0m0.152s

through fusesmb:
real    0m12.442s
user    0m0.008s
sys     0m0.104s

Fusesmb is pretty comparable to gnomevfs-copy, which I think is an indication of how long the same copy would take through Nautilus Places-->Network:
using gnomevfs-copy:
real    0m11.171s
user    0m0.588s
sys     0m0.124s

Fusesmb is a bit faster to my samba server:
real    0m8.886s
user    0m0.028s
sys     0m0.128s

There are some interesting options available if you type fusesmb -h.  Some of them may affect performance, but I couldn't find much documentation on how to use them.  It's probably easier just to mount through cifs for often used and performance critical shares and to use fusesmb for the network-wide convenience value.

---

### Post by peabody on 2008-01-15
fuse filesystems are notoriously slow.  If you need performance, avoid fuse-anything at all costs.

---

