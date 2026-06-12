---
title: "ipod mounting error"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by skydiving85 on 2008-12-14
i changed the mount point name and well added a g_dir_seperator how do i fix this as i cant change it with out remounting it but i cant mount it soo....

---

### Post by kdm on 2008-12-14
Have you tried mounting using the settings menu in Amarok ?

---

### Post by mc4man on 2008-12-14
try running in terminal

```
gconf-editor
```

Look under system -> storage, if you have a listing in either 'drives' or 'volumes' you can edit the key(s)


Edit: if you change the the mount dir. of  a volume or drive thru it's 'properties' you can only specify the new directory name, not it's location.

In screen the default of /media/test was changed to /media/Tester by only adding Tester to mount point in properties of the volume.

---

### Post by skydiving85 on 2008-12-14
thanks

---

