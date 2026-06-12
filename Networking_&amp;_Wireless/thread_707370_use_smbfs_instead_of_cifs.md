---
title: "use smbfs instead of cifs"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by istergiou on 2008-02-25
Hello,
   I want to use smbfs instead of cifs to mount a samba server that supports only plain text authentication. I know that cifs does not do that, therefore I need to use smbfs that can do that. 
When I write
mount -t smbfs ...
the cifs kernel module is loaded and it returns to syslog all messages explaining that it cannot authenticate.
How can I force the use of smbfs instead of cifs kernel module?

I am using hardy with cifs vfs version 1.50. (CIFS with plain text authentication was working fine with feisty with cifs vfs 1.49 but I would not like to discuss this)
Thank you,
Ilias

---

### Post by istergiou on 2008-02-26
I found the way. 
download samba source

# build
./configure --with-smbmount --sysconfdir=/etc/samba --with-lockdir=/var/cache/samba --with-piddir=/var/cache/samba/ --with-configdir=/etc/samba
make 

# backup old helpers
sudo mv /usr/bin/smbmount /usr/bin/smbmount.original
sudo mv /usr/bin/smbumount /usr/bin/smbumount.original
sudo mv /sbin/mount.smbfs /sbin/mount.smbfs.original

# copy new
sudo cp /mnt/sda3/ilias/samba-3.0.28/source/bin/smbmount /usr/bin/smbmount
sudo cp /mnt/sda3/ilias/samba-3.0.28/source/bin/smbumount /usr/bin/smbumount #
sudo cp /mnt/sda3/ilias/samba-3.0.28/source/bin/smbmnt /usr/bin/smbmnt
sudo ln -s /usr/bin/smbmount /sbin/mount.smbfs
sudo ln -s /usr/bin/smbumount /sbin/umount.smbfs 

Now mount -t smbfs will use the smbfs kernel module, not the cifs. Just to explain, I do all this to connect to a server that supports plain text password authentication.

---

