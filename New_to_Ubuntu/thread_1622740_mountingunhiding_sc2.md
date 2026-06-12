---
title: "mounting/unhiding sc2"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by jdav on 2010-11-15
Hi, complete noob here. I am trying to install sc2 on wine atm. I googled and found the whineHQ website and am trying to follow it.

So far it is telling me I must unhide the dvd to pull all the files off of it with this command:
 ```

mount -o ro,unhide,uid=1000 /dev/cdrom /mnt/cdrom

```However when I run that I get this:

 ```
mount: mount point /mnt/cdrom does not exist

```So I am guessing the mount point is incorrect for unbuntu. If so I have no idea what to do. I would really appreciate some help.

Oh and the sc2 dvd is showing up as SC2-L100-D1.

---

### Post by Hippytaff on 2010-11-16
Hi and wleclome.
 
The path to the cdrom should be something like
```

/media/SC2-L100-D1

```
 
to confirm this I would do this
```

cd /media/

```
```

ls

```
Then use that path to unhide and mount

---

