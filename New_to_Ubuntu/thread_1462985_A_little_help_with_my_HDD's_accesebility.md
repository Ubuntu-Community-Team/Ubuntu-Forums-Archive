---
title: "A little help with my HDD's accesebility"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by Xavant on 2010-04-26
Every time i turn on my computer and 'm accesing my slave hdd's ubuntu asks me for my password.
How can i disable that feature, i'm trying to share things on the network and this is preventing accesbility from other computers.

---

### Post by SnickerSnack on 2010-04-26
> **Xavant said:**
> Every time i turn on my computer and 'm accesing my slave hdd's ubuntu asks me for my password.
How can i disable that feature, i'm trying to share things on the network and this is preventing accesbility from other computers.

You're asked for your password when you access the drive, or when you mount the drive?  (You mount the drive first, then you can access it many times.)  Mounting a drive requires an admin password, and I doubt that that can be easily changed.

What sort of network are you using?  Are the other computers linux, windows, mac?

---

### Post by Xavant on 2010-04-26
ok, the others are windows, and they cant acces my shared components, how can i change that?

---

### Post by Grenage on 2010-04-26
Add the drive to *fstab*, then you'll not have to worry about it again.  I could regurgitate a howto, but there are many great guides already out there.  Once mounted at boot, you can share the drive or its directories using Samba, through the GUI.

Just search for *Ubuntu fstab guide*.  fstab isn't just an Ubuntu thing, but guides based around it tend to be more noob-friendly.

---

### Post by P4man on 2010-04-26
Add an entry in your fstab.
Full documentation here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Dont get too scared, its not hard, just add a line to /etc/fstab similar to this one:
```

/dev/sda3       /media/windows  ntfs defaults,locale=en_US.UTF-8     0       0
```

replace /dev/sda3 with your windows partition (or its uuid) and /media/windows with your mountpoint.

---

### Post by SnickerSnack on 2010-04-26
> **Grenage said:**
> Add the drive to *fstab*, then you'll not have to worry about it again.  I could regurgitate a howto, but there are many great guides already out there.  Once mounted at boot, you can share the drive or its directories using Samba, through the GUI.

Just search for *Ubuntu fstab guide*.  fstab isn't just an Ubuntu thing, but guides based around it tend to be more noob-friendly.

Thanks.  This guide was very helpful: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

> **P4man said:**
> Add an entry in your fstab.
Full documentation here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Dont get too scared, its not hard, just add a line to /etc/fstab similar to this one:
```

/dev/sda3       /media/windows  ntfs defaults,locale=en_US.UTF-8     0       0
```

replace /dev/sda3 with your windows partition (or its uuid) and /media/windows with your mountpoint.

After mounting the drive, I looked in /etc/mtab and copied the appropriate line to /etc/fstab.  This ensured that the correct labels were used, and, at least for my setup, I think the additional options present in the mtab entry ensure that the drive shows up in the "Places" menu (or not, maybe all drives mounted at startup will be on that list), if that matters to the OP.

---

