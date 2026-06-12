---
title: "[SOLVED] how do I get 777 rights for fstab smb mount?"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2007-09-20
Good day to all of you! I need to share my resource and give all rights to all users there. I use the following line in fstab:```
//192.168.0.1/Bases /home/user/Bases smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
```But it doesn't give me all rights. I think i should play with uid and umask? What values should I put there? Thank you in advance!

---

### Post by callan79 on 2007-09-20
[QUOTE=PryGuy;3395559fstab:```
//192.168.0.1/Bases /home/user/Bases smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
```But it doesn't give me all rights. I think i should play with uid and umask?[/QUOTE]

Hi,

For smbfs, you need to specify uid=(your-ubuntu-username) and gid=(your-ubuntu-groupname). Note the groupname is probably just the same as your username.

The umask setting is wrong, that's for fat32

But you will need fmask=0777 and dmask=0777

try that :)

Cheers
Callan

---

### Post by PryGuy on 2007-09-21
Thanks bud! You made my day! :) God, what would I do without this forum?!

---

