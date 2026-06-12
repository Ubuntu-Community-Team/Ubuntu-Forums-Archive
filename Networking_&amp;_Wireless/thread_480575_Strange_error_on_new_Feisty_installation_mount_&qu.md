---
title: "Strange error on new Feisty installation: mount: &quot;invalid option -- v&quot;"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by midorigin on 2007-06-21
I'm getting the following error message:
```
me@ubuntu:~$ sudo mount -v /media/Windows-C
/media/Windows-C: **invalid option -- v**
```
but *man mount* lists contradicting information:
```
SYNOPSIS
       mount [-fnrs**v**w] [-t vfstype] [-o options] device dir

OPTIONS
       **-v     Verbose mode.**
```

What's going on?

---

### Post by mitch.c on 2007-06-22
The syntax you used works for me on Edgy. Is it possible you have an invalid option in /etc/fstab and it just _appears_ that -v is causing the error?
[URL="http://ubuntuforums.org/showthread.php?t=377083"][COLOR="Red"]
UAResolved[/COLOR][/URL]

---

### Post by midorigin on 2007-06-24
> **mitch.c said:**
> The syntax you used works for me on Edgy. Is it possible you have an invalid option in /etc/fstab and it just _appears_ that -v is causing the error?
[URL="http://ubuntuforums.org/showthread.php?t=377083"][COLOR="Red"]
UAResolved[/COLOR][/URL]

That shouldn't be it, but I suppose it's possible. This is the only thing I've added to /etc/fstab: (From [this guide]("https://wiki.ubuntu.com/MountWindowsSharesPermanently#head-d14db9e44eb9655a6a09e2c8e936727115340a87"))
```
//192.168.0.10/C    /media/Windows-C smbfs  noauto,username=guest,password=,iocharset=utf8,codepage=unicode,unicode,dmask=777,fmask=777  0    0
```
Think that's the cause of the problem?

---

### Post by mitch.c on 2007-06-25
OK. I misled you. I was mounting using cifs. I switched to smbfs and got the same error. A bit of googling showed many others with the same problem, and some speculation that smbmount is broken. I also found this bug report specifically stating:
```
...bugs related to smbfs which probably will not be fixed...

...smbfs is unmaintained and known to be severely broken. Please use cifs instead
of smbfs...
```
[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Maybe you should drop smbfs in favor of cifs.

Apologies for the confusion.

---

### Post by midorigin on 2007-06-25
Thanks a lot. That fixed it. :)

---

