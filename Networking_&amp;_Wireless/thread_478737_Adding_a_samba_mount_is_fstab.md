---
title: "Adding a samba mount is fstab"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by elev on 2007-06-19
I have been having a real hard time getting my samba shares to mount automatically

I have 
```
//freenas/Media /media/sharedmedia smbfs credentials=/home/jason/.smbcredentials,uid=jason,gid=users 0 0
```
in my /etc/fstab.

When I try ```
sudo mount -a
```

I get back:
> mount: wrong fs type, bad option, bad superblock on //192.168.2.2/Media,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Am I just typing something wrong in fstab?

---

### Post by Sonofmoog on 2007-06-19
Here's a link you may find useful

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

HTH

---

### Post by dmizer on 2007-06-19
you don't yet have smbfs installed.
```
sudo aptitude install smbfs
```
should remedy this problem for you.

you might also consider checking out the second link in my sig.  using cifs instead of smbfs to mount your shares will allow you faster speeds, and larger (bigger than 2gb) file transfers.

---

