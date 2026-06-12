---
title: "quotacheck issue"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by shenchen8571 on 2009-06-14
Hi there, I've download quota and use "quotacheck", there is a problem:
 
```

chen@chen-desktop:~$ quotacheck -uvg /home
quotacheck: Mountpoint (or device) /home not found or has no quota enabled.
quotacheck: Cannot find filesystem to check or filesystem not mounted with quota option.
chen@chen-desktop:~$

```

---

### Post by Ocxic on 2009-06-14
Seems that Quotas are not enabled for your home partition, which would be the norm.
Post the output of "cat /etc/fstab" and I/we can show you how to enable quota for the home partition.

Why do you want to use quotas for your home partition anyways??

---

### Post by shenchen8571 on 2009-06-15
> **Ocxic said:**
> Seems that Quotas are not enabled for your home partition, which would be the norm.
Post the output of "cat /etc/fstab" and I/we can show you how to enable quota for the home partition.

Why do you want to use quotas for your home partition anyway??

I install ubuntu on imac's partition (which is boot ***..) and there is no choice for choosing types of partition. Just for practising "quotacheck". :D

```

chen@chen-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=b7f1ab13-c7a5-4840-ad5c-a2a31747f587 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a61662b5-34a2-4ff1-b4d2-c7266d74694f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

