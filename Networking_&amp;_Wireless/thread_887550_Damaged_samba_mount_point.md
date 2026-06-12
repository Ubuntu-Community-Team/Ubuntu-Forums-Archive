---
title: "Damaged samba mount point"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by mindhaq on 2008-08-12
Hello,

from my Ubuntu laptop I mount a smbd share like this:
```
mount --verbose -t cifs //xx.yy.zz.xx/share ~/mounts/share -o nounix,noperm,username=XYZ,password=XYZ,dir_mode=0777,file_mode=0777,uid=1000
```

Now there has been a problem with the server and it had to be restarted. I tried to umount the share, even with -f, but all it was saying is "device is busy".

After the server restarted, I tried to re-mount the share, but I get the following error:

```
mount error: mount point ~/mounts/share does not exist.
```

Now take a look at the directory ~/mounts/:
```
ls -l
d????????? ? ? ? ?                ? share

```

The question marks are just what I see and no encoding error here...

What can I do to remount a broken share like this without restarting my whole computer? It must be possible to somehow reset this whole cifs subsystem, mustn't there?

---

### Post by Iowan on 2008-08-12
Dunno if **fsck** would help - when I had a weak HD, the "autofix" of **fsck** generally trashed what was left.

---

### Post by mindhaq on 2008-08-13
Hm, using fsck here seems a bit awkward, but who knows?

I'll try when this comes up the next time. For now, I had to reboot the machine to fix this. Which is very annoying.

---

