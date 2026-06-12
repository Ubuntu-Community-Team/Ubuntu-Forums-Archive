---
title: "smbfs mount crashes"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by Subbeh on 2013-09-07
Hi,

I have a smbfs mount in my fstab to automatiicaly mount a directory from another PC on my laptop:

//htpc/ext1 /mnt/htpc smbfs credentials=/home/user/.smbcredentials,uid=1000,gid=1000

However, when my laptop returns from suspend, I can't access the directory anymore and the system just hangs.
I tried remounting it by running umount -a and mount -a but it doesn't do anything. The only way I get it work again is by rebooting the laptop.

Does anyone know how to fix this? 

Thanks

---

