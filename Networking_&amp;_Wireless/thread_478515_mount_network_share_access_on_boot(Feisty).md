---
title: "mount network share access on boot(Feisty)"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by smizak on 2007-06-19
Hi guys, I've recently installed samba to mount a Windows network share on boot, however, even after correctly adding  

//192.168.0.101/sharedfolder /my/mount/folder smbfs defaults 0 0 

to my /etc/fstab, it still will not mount the folder on boot. If I manually enter 

sudo mount //192.168.0.101/sharedfolder  /my/mount/folder -o

or even more curiously

sudo mount -a

all is well.

Thanx in advance,

Damon

---

### Post by DugieHowsa on 2007-06-27
You should try using cifs.  This post states that smbfs is unstable and no longer under active development:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

The following is also a very good post on how to configure cifs and gives a few examples on how to automatically mount cifs shares at boot.

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

