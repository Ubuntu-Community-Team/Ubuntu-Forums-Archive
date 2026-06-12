---
title: "fstab mounting"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by cAllison on 2008-05-01
I am trying to set up fstab to mount some smb shares on a file server.

I am using likewise-open to auth to Win2k AD for logins.
The file server is a Ubuntu Server 6.06 setup with a good deal of samba shares. The file server is working fine. I can connect to it via and windows box and through Nautilis in Gnome(using smb://)

However I cannot mount shares via "mount" (and thus, fstab). I was getting an error saying I needed a proper mount.<fs> file, which I didnt have, so I got the x86 mount.cifs and stuck it in /sbin

Now when I "mount -a" I get no error output, but the share doesn't mount. Here is the fstab entry:

```
//10.73.1.###/Common /mnt/Common cifs rw,-N 0 0
```

I am still a newb, so plz tell me what I am doing wrong. I just want the system to auto mount shares with the users AD creds.

---

