---
title: "how do i keep my /home directory"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by nnamdi on 2010-10-13
i have been using ubuntu since 2008 but i have never done these before now what i want to do is:

1. my system is 320gb of hdd, 4gb of ram...

2. / = 70gb, /home = 240gb, swap = 8gb...

3. now i have all my file in my **/home** directory. but i still want to mount my present home directory as my home directory after installation.... is it possible

---

### Post by TeoBigusGeekus on 2010-10-13
If I understand correctly you want to keep your old /home partition as your new one on a brand new installation.
During installation, in the partitioner, choose manual partition.
Give your 70gb partition a mount point of / and select format partition.
Give your 8gb partition the option of swap partition.
Give your 240gb partition a mount point of /home and **[COLOR="Red"]DON'T FORMAT IT - YOU HAVE BEEN WARNED.[/COLOR]**

I you have an external hd, it would be wise to do a backup first.

---

