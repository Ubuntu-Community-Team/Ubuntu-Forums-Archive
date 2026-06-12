---
title: "Anoying disk checks when booting"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by random turnip on 2009-11-08
Every time i boot into Ubuntu 9.10 it does disk checks, that's fine but i shut my system down properly and instead of just diong the checks, it keeps flashing up at the bottom and doesn't actually do them, just keeps flashing till i press esc.
Any easy solutions?

---

### Post by Barriehie on 2009-11-08
I've got a different version but ```
~ $ > man tune2fs
``` will explain how to set intervals on the file system check.  Whether or not the filesystem is checked is set in your /etc/fstab when the partition is mounted.

Barrie

---

### Post by peculiar penguin on 2009-11-08
Post the output of
```
sudo tune2fs -l /dev/sda1 | grep -i "mount count"
```and
```
sudo tune2fs -l /dev/sda1 | grep -i check
```Replace sda1 with the appropriate partition(s).

---

### Post by hal10000 on 2009-11-08
```

sudo tune2fs -c 100 -i 90d /dev/sda1

```

this example sets the filesystem check to be done either at every 100th boot process or to an interval of 90 days

---

### Post by benj1 on 2009-11-08
if youre on ext3 and feel like a reinstall, change your file system to ext4 it wont stop the checks but makes them significantly faster

---

### Post by think13 on 2009-11-08
I have the same problem. In Karmic, it starts a filesystem check on every boot, and the check does not work. From Jaunty, you could see the progress of the check, but it always stays at 0% progress in Karmic. I would rather not reinstall to switch to ext4.

Poking around in /var/log, I didn't see anything that jumped out at me.
The filesystem it seems to be having trouble with is my home partition, if that makes any difference.

---

