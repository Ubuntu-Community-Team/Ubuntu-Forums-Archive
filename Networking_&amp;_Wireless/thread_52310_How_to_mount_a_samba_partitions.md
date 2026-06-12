---
title: "How to mount a samba partitions"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by xeo_pt on 2005-07-27
Hi,
I have a file server (with samba) where is as a share call mp3.
How can i mount the share in my ubuntu machine (desktop) in a way that I use it as a normal directory.

Thanks in advance.

xeo

---

### Post by PeP on 2005-07-27
install smbfs:
sudo apt-get install smbfs


if you want to mount it in /mnt/mp3_samba
```

mount -t smbfs -o username=john,password=doe,workgroup=co //server/com3 /mnt/mp3_samba

```
you can mount it automatically by adding a line in /etc/fstab
```

//server/com3    /mnt/mp3_samba  smbfs auto,users,username=john,password=doe,workgroup=co  0  0

```

---

### Post by xeo_pt on 2005-07-27
That's it.
Thank you.
 :razz:

---

### Post by PeP on 2005-07-29
you're welcome :-)

---

