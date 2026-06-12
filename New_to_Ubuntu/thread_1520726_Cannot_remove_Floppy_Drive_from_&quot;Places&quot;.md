---
title: "Cannot remove Floppy Drive from &quot;Places&quot; menu."
date: 2010-06-29
forum: New to Ubuntu
---

### Post by kirbyparufo on 2010-06-29
I had previously removed the Floppy Drive from my "Places" menu by altering the following line (or a similar one, it's been a while) by placing a # in front of it in fstab:

```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```However, the Floppy drive reappeared mysteriously after downloading the latest set of updates via the Update Installer (or whatever it is called). I went to my fstab, but the line has completely vanished and I cannot figure out how to remove the Floppy Drive from the "Places" menu. If I could, I'd like to remove the floppy drive from my system entirely (in fact, it doesn't have one), but if that is impossible I'd just like to remove the thing from "Places" again so I don't keep hitting it when trying to access my Computer icon. Here is my current fstab:

```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
UUID=0d484196-0f93-4bc7-ac2e-b024241f9294 none            swap    sw              0       0

```EDIT: Entering either of the following (as I saw another user did with success) in the terminal removes the drive, but the drive reappears whenever I restart/shut down. Is there a permanent fix for this?

```
sudo modprobe -r floppy
sudo rmmod -f floppy
```

EDIT #2: I think I've found a walkaround for this. Editing rc.local in /etc/ by adding the following line appears to keep the drive from loading:

```
rmmod -f floppy
```

---

