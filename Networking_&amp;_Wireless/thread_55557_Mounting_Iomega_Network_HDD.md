---
title: "Mounting Iomega Network HDD"
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by 1337G33K on 2005-08-09
Hi all!  I'm a linux n00b, and since I switched over from WinXP last weekend, I've been LOVING this distro! :D

I have a Iomega Network HDD (160GB):
[http://www.iomega.com/direct/products/detail.jsp?PRODUCT%3C%3Eprd_id=17981417&FOLDER%3C%3Efolder_id=26891315&ASSORTMENT%3C%3East_id=63191&bmUID=1123599644918](http://www.iomega.com/direct/products/detail.jsp?PRODUCT%3C%3Eprd_id=17981417&FOLDER%3C%3Efolder_id=26891315&ASSORTMENT%3C%3East_id=63191&bmUID=1123599644918)

When I go to Places->Network Servers->Windows Network , I can see my drive (shows up as a Samba shared drive, NTFS formatted).  But how do I mount it permanently?  (i.e. to say... /mnt/mp3/)

Thanks in advance!

---

### Post by jasmuz on 2005-08-09
Hey dude..
Check this out, it might help you.

[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

### Post by 1337G33K on 2005-08-11
Hi jasmuz, I checked out the link you've provided, but none of the commands worked:

```
.: gene@prometheus :.
/mnt ->sudo smbmount //titan/NetHDD /mnt/titan
sudo: smbmount: command not found
```

Next, I tried:

```
.: gene@prometheus :.
/mnt ->sudo mount -t smbfs //titan/NetHDD /mnt/titan
mount: wrong fs type, bad option, bad superblock on //titan/NetHDD,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Please note that this is a NAS and has no username or password for login.  "titan" is the name of the "machine", and "NetHDD" is the shared folder.

Any suggestions?

Thanks again!

---

### Post by 1337G33K on 2005-08-13
Bump!

---

