---
title: "[SOLVED] problem mounting a samba share: invalid share name"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by ARhere on 2007-12-16
All,

I am positive that I am missing something really simple.  I am trying to mount a samba share.  The command I type is...
```
sudo mount -t smbfs -o username=xxx,password=xxxxxx //fileserv/Music /home/jill/Music

```
and the response is...
```
jill@Dell4500:~$ sudo mount -t smbfs -o username=xxx,password=xxxxxx //fileserv/Music /home/jill/Music
21282: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

```

I have double checked, and the owner of **/home/jill/Music** is user jill, and I have no trouble accessing the share using Nautilus, it is listed as **smb://fileserv/Music**.

Spelling error anyone?
-ARhere

---

### Post by ARhere on 2007-12-16
SOLVED!

For some reason the server shares was flagged "unusable" in smb.conf even though the GUI said all was good.

I guess I just learned that nothing beats command line!

-AR

---

### Post by bpowell1978 on 2008-02-02
I am having the same exact problem and cannot figure it out.  What exactly did you edit in your smb.conf file?

---

