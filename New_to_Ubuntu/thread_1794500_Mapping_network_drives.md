---
title: "Mapping network drives"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by twhansen on 2011-07-01
Hi.

I am desperately trying to map network drives from Ubuntu on my laptop. How does that work? I read something about Samba, but when I tried it I killed my Ubuntu partition bigtime.

Hope someone can guide me in the right direction.

Thanks.

Thomas

---

### Post by mobius129a on 2011-07-01
Try ```
smbtree
``` in a terminal. For options to the command see tha man page for smbtree (man smbtree).

---

### Post by Gone fishing on 2011-07-01
You need to mount the share I use a Linux server and nfs which think is the best way of doing it. However, if you are try to connect to a Windows share on a Windows server these links should help:

[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

