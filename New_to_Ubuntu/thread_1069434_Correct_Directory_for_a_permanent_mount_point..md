---
title: "Correct Directory for a permanent mount point."
date: 2009-02-14
forum: New to Ubuntu
---

### Post by JagDragon on 2009-02-14
Hey All,

I'm about to edit my fstab to mount some network shares on startup. I was wondering, since everything has a correct/conventional spot in linux, in what directory should I make my mount points? The two points are music and pictures, but I don't know what the convention is (or if one even exists) for permanent mount points for network shares.

Thanks.

---

### Post by jerome1232 on 2009-02-14
/mnt is for permanent mounts

/media is for removable disks

Actually it doesn't matter though the main difference is things mounted under /media and in your $HOME will show up with icons on you desktop and with an entry in your places menu. Disk mounted anywhere else but those two locations don't get desktop icons and an entry in the places menu.

---

