---
title: "Change order of rc#.d startup for networking"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by strangeion on 2007-07-18
I'm trying to do mount some SMB shares through fstab, but it doesn't work correctly at boot. If I mount them manually with **mount -a** it works fine. I'm thinking the problem is that networking is initializing after the fstab file is processed.

I can't quite figure out which script in rc2.d initializes networking. Any help or suggestions?

---

### Post by t4thfavor on 2007-07-18
I believe that networking is wet up in /etc/init.d/  
Try looking at the "networking" file. I am not aware how to change the startup order, nor would I recommend it. The Ubuntu team has it set up the way its supposed to work,

---

### Post by strangeion on 2007-07-18
The networking script in init.d doesn't help me much. It's simply initializing all the different things that go into networking. I'm trying to figure out why my SMB shares will not auto mount at boot. I've checked my logs and there are no errors.

Here's one of the entries from my fstab. Maybe there's something I'm missing?

```
//192.168.1.210/juan /media/moya/juan cifs auto,credentials=/home/juan/.smbpasswd,uid=juan,gid=juan 0 0
```

---

### Post by fredj on 2007-07-18
I think the init files in init.d are fired off by symbolic link files in the rc#.d directories and these are processed in
numerical order i.e. the S50,S55 links fire before the S60,S61 links and the links in rc1.d should fire before
those in rc2.d.  So if you know the name of your network init script in init.d you can find the link file in some 
rc#.d directory and try renaming it or even moving it.

However as with all these things better make a backup before making changes.

---

