---
title: "System crashed and will not let me in"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by Jonluv on 2010-07-25
Any who can help me please
 
Put Ubuntu 10.4 on a couple of days ago and every thing was fine untill I started update manager and loaded a batcg of files.
 
The Computer restarted and went to a black scree that said o-597258] kernel panic-not syncing:vfs:unable to mount rlot:-( on unknown-block(0,0) 
 
Restarted with "restore" menu and got cannot open sda5.
 
In both cases I could not type anything on the black screen
 
Many thanks

---

### Post by cariboo on 2010-07-25
Boot from the Live CD and once at the desktop open a terminal and type:

```
sudo fsck -y /dev/sda5
```

Once it has finished, you should be able to reboot and return to your desktop.

---

