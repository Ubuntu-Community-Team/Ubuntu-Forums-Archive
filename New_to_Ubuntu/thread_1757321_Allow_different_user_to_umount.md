---
title: "Allow different user to umount"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by JamieKitson on 2011-05-13
Hi,

I have a disk with the "user" option in fstab, but I want to allow a different user to umount it to the one that mounted it, which at the moment I can't. Is that possible?

Thanks, Jamie

---

### Post by quixote on 2011-05-14
I think it's possible.  Not sure actually.  There's some subtle difference between "user" option and "users". (I can never remember what.)  Try the latter.  Another way to specify user permissions even more strongly is "uid=1000,gid=1000," (="any user or group who is not root") or "uid=0,gid=0," (absolutely any user or process on the system).  The latter is probably a big security hole, but you could try it just to see if unmounting by a different user can work at all.

---

### Post by JamieKitson on 2011-05-14
Thanks very much, the "users" option worked a treat.

---

