---
title: "File (not /ect/fstab) that holds Nautilus mount options?"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by hobo14 on 2009-03-31
I was changing some mount options for my external hard disk, but instead of creating an entry for it in /etc/fstab I just right-clicked on its icon, Properties > Volume > Settings, and entered the options in the mount options box.

Unfortunately I made a typo, and now the disk won't automount, it says "invalid mount option".  I can force mount it through terminal, but I still don't get an icon on the desktop where I can go and fix my typo.

Can somebody please tell me which file Nautilus stores these extra options in? It's not /etc/fstab, I don't have an entry for this disk in there.  I did try putting one in, hoping that it would override the Nautilus options, but it didn't work.

I assume the file is somewhere in my home directory, because if I log in as root everything works fine, I am the only user with the problem.

So I have no automount, and no gui access to the disk until I can find that file..... :(

---

### Post by unutbu on 2009-04-01
Look in the directory
```

~/.gconf/system/storage/volumes
```

for a subdirectory with a name like
```

_org_freedesktop_Hal_devices_volume_uuid_**5F3A5E5E63454964**_0

```
(Your UUID (the part in bold) will be different.)

To get your system back to normal, you can delete this subdirectory.

---

### Post by hobo14 on 2009-04-01
Cheers unutbu ;)

---

### Post by Debiant666 on 2009-06-15
Nice one , took me a while to figure that one out .. was bugging me for ages.

---

