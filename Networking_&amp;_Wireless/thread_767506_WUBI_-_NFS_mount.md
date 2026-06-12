---
title: "WUBI - NFS mount"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by sheridon on 2008-04-25
Hi all,

I am new to ubuntu but not to linux, I just installed WUBI on my laptop and am trying to mount my linux share on a Fedora machine that worked when Fedora was installed on my laptop.

I edited my /etc/fstab file and added

192.168.15.101:/media/save/Music  /media/Music  nfs  defaults 0 0

saved the file then performed

sudo mount -a

then the terminal will just sit there doing nothing till I stop it....

Any ideas?

Thanks in advance

---

