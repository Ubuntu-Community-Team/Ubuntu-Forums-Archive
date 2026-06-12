---
title: "Unable to mount a Synology DS-101 share after upgrade"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by NarsilAnduril on 2008-05-30
Hello,

Simple but annoying :

I have an Synology DS-101 NAS and on my first machine running Gusty I can mount without problems the smb shares with a 

```
//172.26.155.5/public /mnt/NAS1/public smbfs credentials=/home/me/.smbpasswd,uid=me,gid=me 0 0
```
(note thats cifs donesn't work with this old NAS

But this doesn't work on Hardy. Did anything change between smbfs
3.0.28a (Hardy's version) and 3.0.26a (Gusty's) ?

Diego

---

### Post by dmizer on 2008-05-31
smbfs has depreciated and is not included in hardy.  if you need to have smbfs in order to mount your nas device, you will have to compile it yourself.

here's more information: [http://ubuntuforums.org/showthread.php?t=707370](http://ubuntuforums.org/showthread.php?t=707370)

---

### Post by NarsilAnduril on 2008-06-02
Done, works.

Thanks dmizer

---

