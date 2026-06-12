---
title: "Unable to mount"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by bj218 on 2010-11-28
I have 2 partitions that I can not mount & the attachment shows what I get when I try to see them.

---

### Post by sikander3786 on 2010-11-28
This might help.

[http://ubuntuforums.org/showthread.php?p=9376116](http://ubuntuforums.org/showthread.php?p=9376116)

---

### Post by bj218 on 2010-11-28
> **sikander3786 said:**
> This might help.

[http://ubuntuforums.org/showthread.php?p=9376116](http://ubuntuforums.org/showthread.php?p=9376116)

This did not help!! I don't have an external HD & I don't want to remove
all my programs on these partitions. Is there something else I can try?

---

### Post by sikander3786 on 2010-11-28
Please post the output of these commands.

```
ls -l /media
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by bj218 on 2010-11-29
> **sikander3786 said:**
> Please post the output of these commands.

```
ls -l /media
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

I hope this is what you wanted.

---

### Post by bj218 on 2010-11-29
I just checked & all the partitions on my C drive are accessable. I don't know how
this happend but it looks like everthing is working again.

---

