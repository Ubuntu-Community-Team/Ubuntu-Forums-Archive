---
title: "installing applications on memory card"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by ibeacco on 2009-07-20
i have a very small HD on my netbook and i'll like to install any new application on the memory card by default. How can i do that? Can i migrate any other folder on the MC so that i can free some space up on the HD?
I'm running Ubuntu 9.04
Thanks
Ivan

---

### Post by bacil on 2009-07-20
mount your /usr filesystem from MC.

you will need to copy your current /usr to MC and then mount it to /usr and then edit fstab to mout this every boot.

something like this

```
 cp /usr /media/disk
```

my MC is mounted to /media/disk

then

```
mount /dev/mmcblk0p1 /usr
```

and tehn edit fstab

```

vi /etc/fstab

/dev/mmcblk0p1    /usr   ext3   0      0      0

```

---

