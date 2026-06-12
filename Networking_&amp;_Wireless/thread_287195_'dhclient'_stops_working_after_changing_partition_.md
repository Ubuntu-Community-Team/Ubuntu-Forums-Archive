---
title: "'dhclient' stops working after changing partition UUID, or after tar/untar"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by Siilex on 2006-10-28
Can somebody explain this?
Can somebody replicate this?

Install Ubuntu 6.10 Server without tasks, the minimum.
Now, dhclient works, and gets an IP for eth0.

Using grub, boot in another system, mount the partition, and .tgz the entire directory tree of the partition. (That is, make a backup of the fresh installation).

$ mount /dev/hdb1 /mnt/hdb1
$ cd /mnt/hdb1
$ tar -czf /root/ubuntu.tgz *

Umount, reformat the partition, mount again, and untar the files in. (That is, simulate a desaster, and a recovery of the fresh installation).

$ cd /
$ umount /dev/hdb1
$ mke2fs /dev/hdb1
$ mount /dev/hdb1 /mnt/hdb1
$ cd /mnt/hdb1
$ tar -xzf /root/ubuntu.tgz

Edit fstab, because in 6.10, volumes are named with UUID, and put '/dev/hdb1' instead, for the root partition. 

Shutdown, and using grub, reboot into the ubuntu installation.

Now dhclient doesn't work anymore.

Despite of this, it's also posible to configure eth0 with the usual:

$ ifconfig eth0 192.168.0.10
$ route add default gw 192.168.0.1
 
.

---

### Post by lloyd_b on 2006-10-28
Suggestion: After booting, run:
```
sudo /etc/init.d/networking restart
```
and capture the error messages (I'm assuming that there are going to be some).

Hopefully that will provide a clue...

Lloyd B.

---

### Post by Siilex on 2006-10-28
Thanks, you are right.

I fount it.
For some reason, **/lib/dhcp3-client/call-dhclient-script** 
in ubuntu 6.10 is of group **crontab**, while 
in ubuntu 6.06 is of group **dhcp**, and that makes sense.

So this two lines seem to fix it: (completely?)

```

sudo chgrp dhcp /lib/dhcp3-client/call-dhclient-script
sudo chmod u+s  /lib/dhcp3-client/call-dhclient-script

```

I don't know if it's a bug, or only my fault.
If it's a bug, and someone knows where and how to fill the bug form, please, do it for me.

---

