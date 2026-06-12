---
title: "Superblock Error"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by austin501 on 2011-06-21
I am trying to mount an xfs array from a My Book World Edition NAS and I am receiving the following message:

```

root@ubuntu:~# mount -t xfs /dev/sdb4 /media/xyz
mount: /dev/sdb4: can't read superblock

```

My only goal is recover my files Not sure if there is another workaround. 
I found this website which had some information.
[URL="http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/" ]http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/ 
[/URL]
Here is what is returned in terminal:

```

dumpe2fs 1.41.14 (22-Dec-2010)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sdb4
Couldn't find valid filesystem superblock.

```

I am not sure what I should try next?

---

### Post by jtarin on 2011-06-21
> **austin501 said:**
> I am trying to mount an xfs array from a My Book World Edition NAS and I am receiving the following message:

```

root@ubuntu:~# mount -t xfs /dev/sdb4 /media/xyz
mount: /dev/sdb4: can't read superblock

```
[Refer to your system log file (/var/log/messages) for a detailed diagnostic message from the kernel]("http://xfs.org/index.php/XFS_FAQ")

---

