---
title: "Samba, Only root can write to share"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by latle on 2007-05-01
First of all, yes I have searched and tried to find this thing out! :-)

I followed [this thread]("http://ubuntuforums.org/showthread.php?t=288534&highlight=only+root+write+access+shares") on how to set up shares in fstab using cifs and smbcredentials.

The problem is that I can't figure out how to make the share writeable for my non-root-user. I have only read-access with my non-root.

my fstab:
```
//serverko/leif    /media/serverko        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

and my smbcredentials file contains my username and password for my share.

The share (a NSLU2 NAS running unslung) is reached from other boxes (winxp, vista and xbox) so all should work just fine there.

---

### Post by latle on 2007-05-01
some help? :-)

---

### Post by dmizer on 2007-05-02
try adding the "rw" (readwrite) option like so:
```
//serverko/leif    /media/serverko        cifs    credentials=/root/.smbcredentials,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
please do let me know if that fixes your problem.  if not, please post in the howto and i'll be happy to help you out.

---

