---
title: "mounting smb file system password help"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by revelation.now on 2007-04-23
Hi all,
I've added some mounts in /etc/fstab 

//revelation/music1 /mnt/music1

and I can mount that manually:
sudo mount /mnt/music1

but when I reboot I get a HAL failure when gnome starts which I have traced to these devices probably requiring some additional password information since they don't automount on boot and when I comment the additions back out of fstab the HAL notifications cease. I assume its because its attempting to mount these file systems and failing due to a password being required to access the shares

whats my grief? Thanks

---

### Post by ABCC on 2007-04-23
If you're mounting these directories from a samba fileserver then you'll need to either ensure that you have a user account on that server to access the directories, or set up to not use passwords. See [http://www.debuntu.org/guest-file-sharing-with-samba](http://www.debuntu.org/guest-file-sharing-with-samba) for more details.

---

