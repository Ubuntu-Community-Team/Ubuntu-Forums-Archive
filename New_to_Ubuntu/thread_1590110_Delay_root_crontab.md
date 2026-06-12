---
title: "Delay root crontab"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by MrWES on 2010-10-07
I have a root crontab that currently states:

@reboot mount /dev/sdb1 /media/external

I actually need to delay that say 60 seconds, as grub keeps reassigning my /dev when it sees the sdb1 first and called it /dev/sda1. Any thoughts?

Thanks,
Bill

---

### Post by CharlesA on 2010-10-07
Mount by UUID instead of /dev/sdxy.

You can find the UUID by running this:

```
sudo blkid -c /dev/null
```

Are you doing it this way to get around the deal where it hangs if it cannot find a device listed in fstab?

---

### Post by MrWES on 2010-10-07
> **CharlesA said:**
> Mount by UUID instead of /dev/sdxy.

You can find the UUID by running this:

```
sudo blkid -c /dev/null
```

Are you doing it this way to get around the deal where it hangs if it cannot find a device listed in fstab?


Bingo -- fixed. 

Danke!

---

