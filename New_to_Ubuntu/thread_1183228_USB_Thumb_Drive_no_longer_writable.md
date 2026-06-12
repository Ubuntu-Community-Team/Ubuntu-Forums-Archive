---
title: "USB Thumb Drive no longer writable?"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by TomR55 on 2009-06-09
I'm running 8.10/9.04 (64-bit) version. I've been using rsync to back-up files between machines on USB thumb drives for some time with no problems.

Now, for no apparent reason, I can no longer write to this thumb drive because the permissions have changed: group is now "root" although the owner name has stayed the same. Attempts to chmod -R +rw fail with "read only filesystem" messages for each file.

I note, in passing, that other thumb drives work ... this one, for mysterious reasons, just stopped working. I wouldn't mind if I'd done something, but random failures like this are troubling.

Any ideas?

TomR

---

### Post by jman6495 on 2009-07-06
did you use SUDO chmod ???

---

### Post by prshah on 2009-07-06
> **TomR55 said:**
> 
Now, for no apparent reason, I can no longer write to this thumb drive 

If the thumb drive is fat32, (vfat) you may need to run an fsck on it. Plug it in, then unmount it. Check in the dmesg ( dmesg | tail ) for the device ID eg, /dev/sdf1.

Run an fsck on it```
sudo fsck -r /dev/sdf1
``` If you would prefer an automatic repair (may lose some files, data, doesn't work always) you can use "-a" instead of "-r"

You may have to run it twice or more until you get no errors at all.

A backup of the current contents before you start is a good idea.

---

