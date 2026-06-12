---
title: "DNS-323 network storage mounting problem"
date: 2013-10-12
forum: Networking &amp; Wireless
---

### Post by Janiporo on 2013-10-12
So I use this to mount my drive in /etc/fstab:
```
//192.168.1.100/Volume_1-1  /media/stg5  smbfs  username=admin,password=XXXX,uid=1000,iocharset=utf8,unicode 0 0
```

From one computer (Linux Mint) it mounts fine, but not from the Ubuntu machine. What should I try next?

Synaptic tells me smbfs is installed.

  Does it matter that it is mounted from one place already for admin, and I can not login at the same time with another admin? (I tried to unmount the drive from Mint, and it still does not mount to Ubuntu. So maybe this is not the problem.)

All it says is:
```
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

How can I manually try this mount from terminal? I forgot, it might give better picture what is happening.

EDIT: /var/log/kern.log says:
```
Oct 13 00:25:38 xbmc-htpc kernel: [115819.385132] CIFS: Unknown mount option "unicode"
```
So I am looking for that option now

---

### Post by Janiporo on 2013-10-12
I just removed the "unicode" text from fstab and changed smbs to cifs and now it works :D

---

### Post by mörgæs on 2013-10-13
Thanks for an attempt to mark the thread 'solved'. The best way is using Thread Tools, though.

---

### Post by Janiporo on 2013-10-13
Oh, did not know that, better now? :P

---

