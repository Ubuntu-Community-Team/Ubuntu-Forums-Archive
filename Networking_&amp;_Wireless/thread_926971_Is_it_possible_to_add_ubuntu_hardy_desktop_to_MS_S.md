---
title: "Is it possible to add ubuntu hardy desktop to MS SBS domain?"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by echo-gecko on 2008-09-22
Hi all
Is it possible to add ubuntu hardy desktop to MS SBS domain?
Or at least get it to connect to my sbsbox so I can share files between the two machines?
Thanks! Echo

---

### Post by veloce on 2008-09-24
Yes it is possible, but easier not to.

You should be able to connect to shares on your sbs box through the Places\Network menu - you should see "Windows Network" and you can browse to the share you want.  You will be asked for a username and password for your domain.

You can also mount shares into your ubuntu file system by editing /etc/fstab.  I think the instructions are on this forum somewhere - search for smbfs or cifs.

---

