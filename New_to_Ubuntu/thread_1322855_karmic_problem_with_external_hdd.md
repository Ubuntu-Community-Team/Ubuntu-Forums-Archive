---
title: "karmic: problem with external hdd"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by infernus_crusher on 2009-11-11
it only mounts when if i plug it in before booting. if i remove it with either "unmount" or "safely remove drive", unplug and plug it in again, it'll try to start for about 10 seconds, and then die.

how do i manually mount it afterwards?

---

### Post by Joe Ker1086 on 2009-11-11
Depending on how you want to mount it you can try something like this. make adjustments as necessary to fit how you have it mounted initially.

```
mkdir /media/usb_drive
```

Add this line in /etc/fstab file :


```
/media/disk   /media/usb_drive  vfat   noatime  0 0
```

WHERE IT SAYS DISK ENTER THE LOCATION OF YOUR DRIVE ie /media/sda1

Let me know if that works.

---

### Post by infernus_crusher on 2009-11-11
Doesn't seem to work. This is what I did.

```

sudo mkdir /media/a6ad5acf-9d9e-4ff9-982b-f76f175d6208

```

The random alphanumerical combination was what the drive was when it was mounted initially.


Then I added the following line /etc/fstab.

```

/dev/sda2		/media/a6ad5acf-9d9e-4ff9-982b-f76f175d6208		vfat	noatime		0	0

```

Made no difference really.

---

### Post by infernus_crusher on 2009-11-11
I had almost the same /etc/fstab file on Jaunty partition (with the exception of the current partition on which the OS is installed), but with the same fstab file my external HDD doesn't work on Karmic. Weird.

---

### Post by infernus_crusher on 2009-11-11
nvm turns out that it's on sdb, not sda2

---

### Post by Joe Ker1086 on 2009-11-13
So did that end up working now?

---

