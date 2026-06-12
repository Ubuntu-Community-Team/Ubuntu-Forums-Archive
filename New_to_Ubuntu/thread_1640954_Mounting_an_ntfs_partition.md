---
title: "Mounting an ntfs partition"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by japhyr on 2010-12-08
Hello,

I have an ntfs partition that is used for data shared between ubuntu and windows.  I have looked at a number of examples, but I am not entirely sure what options to list in the fstab line for this device.  The partition is working, in that I can save to and read from the partition in ubuntu.  However, I get an error about the partition on startup.  Are there any changes I need to make to this line of fstab?

```
UUID=### /home/username/all_data ntfs defaults 0 0
```

---

### Post by TeoBigusGeekus on 2010-12-08
Looks legit, what error messages do you get?

---

### Post by sikander3786 on 2010-12-08
Make sure the UUIDs match.

See in the output of this command.

```
sudo blkid
```

And compare it with the entry in /etc/fstab.

---

### Post by japhyr on 2010-12-08
> **sikander3786 said:**
> Make sure the UUIDs match.
Thank you, this was the issue.  I kept seeing lines like this:
```
UUID=72312211123E6161 /drive/data ntfs-3g rw,users,uid=1000,gid=1000,dmask=0000,fmask=0007,auto 0 0
```I wondered if I needed something like a uid=### in there, or if defaults took care of all that.

---

### Post by sandyd on 2010-12-08
> **japhyr said:**
> Thank you, this was the issue.  I kept seeing lines like this:
```
UUID=72312211123E6161 /drive/data ntfs-3g rw,users,uid=1000,gid=1000,dmask=0000,fmask=0007,auto 0 0
```I wondered if I needed something like a uid=### in there, or if defaults took care of all that.
you know that the 'users,rw' options are sufficient right?

---

### Post by japhyr on 2010-12-08
> **sandyd said:**
> you know that the 'users,rw' options are sufficient right?

No, I was not sure which options were sufficient.  Is this effectively what I have done with the line I have:
```
UUID=### /home/username/all_data ntfs defaults 0 0
```or should I have something more like this?
```
UUID=### /home/username/all_data ntfs users,rw 0 0
```

---

