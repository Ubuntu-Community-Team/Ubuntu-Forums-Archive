---
title: "Am i using correct syntax for mounting my drives?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by legolas_w on 2008-12-04
Hi
Thank you for reading my post.
Please let me know whether my syntax is correct for mounting a windows partition in ubuntu 8.10. I search the web and I found this syntax which was from 2006, so I though I should confirm that the syntax is correct before harming my drives.
```

/dev/sda5 /media/dev ntfs-fuse auto,gid=1002,umask=0002 0 0

```
the above command shoud mount sda5 to media/dev in read and write mode.


```

/dev/sda5/all /media/all ntfs-fuse auto,gid=1002,umask=0002 0 0

```
I moved all content of an ntfs partition named all to a folder inside sda5, now I want not to lose all music libraries which are present in amarok so I want to use the same directory inside /media/ to mount all folder which I was using to mount "all" partition. (Ubuntu was mounting it not me :P )
Will it work? is the syntax correct?


Also, can you please let me know what is the meaning of the following line:

```

UUID=75794903-5d98-4dec-a9d1-dded76ce5229 / ext3 relatime,errors=remount-ro 0 1

```

And finally my last question, how I can mount the /opt/ to another place? for example mount it to another partition? (I can ensure that no file is open when I am changing the mount point) I want to move all of its content to another partition and use that partition as my /opt/ folder.


Thank you

---

### Post by hrod beraht on 2008-12-04
> **legolas_w said:**
> 
Also, can you please let me know what is the meaning of the following line:

```

UUID=75794903-5d98-4dec-a9d1-dded76ce5229 / ext3 relatime,errors=remount-ro 0 1

```


That's the fstab line to mount your root partition (/). The UUID is a uniquie identifier created when you made the file system. It's simply another way to identify the partition, but unlike using something like /dev/sda1, it is wholly unique and never changes. The association between the mount point and the partition is more robust when using UUID's.

Bob

---

### Post by bodhi.zazen on 2008-12-04
Never is a long time :)

The UUID changes if the partition is (re)formatted.

This, IMO, most often occurs when the swap partition is formated when installing another linux distro.

---

### Post by legolas_w on 2008-12-04
Hi

Any comment for my other questions?

Thanks

---

### Post by bodhi.zazen on 2008-12-04
Personally I would make an /opt in your $HOME ...

If you wish to move it, I advise you use a live CD. It *may* be easier to just re-install and set up your partitions "manually".

Otherwise, make a new partition, move the data, and edit fstab.

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by linux_tech on 2008-12-04
This is a good guide for Adding a Hard Drive in Linux and also covers mounting and formatting
[http://www.skullbox.net/newsda.php](http://www.skullbox.net/newsda.php)

---

