---
title: "Can't transfer large files over mount samba folder"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by taddy_porter on 2006-11-23
I frequently move large files (ripped dvds mostly) to a Windows MCE box I have mount locally. It always craps out at 2gbs. 

The only way I can get it to transfer completely is to browse to the network shares and transfer it that way. I don't know where to look for configs on this. Can anyone help? Below is my fstab:

```
//htpc/D /home/taddy/htpc smbfs uid=taddy,gid=users,username=defaults,password=defaults,fmask=666,dmask=777 0 0
//htpc/D /home/taddy/flac smbfs username=defaults,password=defaults 0 0
```

---

### Post by msak007 on 2006-11-23
> **taddy_porter said:**
> I frequently move large files (ripped dvds mostly) to a Windows MCE box I have mount locally. It always craps out at 2gbs. 

The only way I can get it to transfer completely is to browse to the network shares and transfer it that way. I don't know where to look for configs on this. Can anyone help? Below is my fstab:

```
//htpc/D /home/taddy/htpc smbfs uid=taddy,gid=users,username=defaults,password=defaults,fmask=666,dmask=777 0 0
//htpc/D /home/taddy/flac smbfs username=defaults,password=defaults 0 0
```
Not sure if this will help you as I don't mount any Windows shares locally, but I've read and heard that mounting shares using CIFS instead of SMBFS resolves some of the issues. I believe one of those issues seems to be a 2gb / 4gb bug when transferring files. I've copied files over a network before by browsing to a network share, and have had the file transfer eventually error out (can't recall if it was 2gb, sure it was more). Try replacing smbfs with cifs in your fstab and see if that resolves the issue.

---

