---
title: "[SOLVED] Problem with NFS mount"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by aznewsh on 2007-11-26
If I run the following command:

sudo mount 192.168.2.4:/home/myid /mnt/myshare


I get this error:

mount.nfs: rpc.statd is not running but is required for remote locking.
   Either use '-o nolocks' to keep locks local, or start statd.

Any thoughts?

Thanks

---

### Post by aznewsh on 2007-11-26
nevermind - my bad

sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart

fixed it, hope this helps someone down the road

---

