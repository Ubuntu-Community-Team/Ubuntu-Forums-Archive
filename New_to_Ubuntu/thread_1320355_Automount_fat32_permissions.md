---
title: "Automount fat32 permissions"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by celticbhoy on 2009-11-09
I have aet a fat32 partition to automount setting up fstab as :-

/dev/sda5 /media/SHARED default 0 0 

the patition automounts, but it has root permissions, how do I fix this ?

---

### Post by scragar on 2009-11-09
```
/dev/sda5 /media/SHARED vfat sync,nodev,nosuid,user,rw,auto 0 0
```

Oh, sorry I never actually explained on that line, that should be added to your /etc/fstab file, some parts of it can be left off, they are actually unneeded since they are defaults, like sync, rw and auto, but specify them anyway, just to be sure.
```
gksu gedit /etc/fstab
```
Delete the current line and add that one in it's place.

---

### Post by hijudoboy on 2009-11-12
I'm having the same problem but modifying the code didn't help.  Is there anything else I can try?

---

