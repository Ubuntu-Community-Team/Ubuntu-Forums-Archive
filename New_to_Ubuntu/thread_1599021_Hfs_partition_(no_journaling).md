---
title: "Hfs partition (no journaling)"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by maszy on 2010-10-17
Hello,
I just formatted my external hard drive in HFS unjournaled and when I connect the hd, I can't write files but only read.
I tryed with sudo nautilus and it works.

Now, what I have to do to use the drive without the sudo command?

I searched a lot in the forum but I find a lot of difference replies (and no one that I tryed seems works)

Many Thanks

Massimiliano

---

### Post by srs5694 on 2010-10-18
```

sudo chmod 0777 /media/hfs

```

Change the mount point as necessary, of course. Alternatively, you can use chmod to change the permissions to something more restrictive and change the group and/or user ownership, as in:

```

sudo chmod 0750 /media/hfs
chgrp somegroup /media/hfs
chown someuser /media/hfs

```

This would give someuser read/write access to the partition, everybody in somegroup read-only access, and blocks everybody else from accessing it at all. There are many variants of this possible.

Note that if OS X will be accessing the disk, it's got its own usernames and group names. It's often useful to synchronize the username/UID and group name/GID mappings between Linux and OS X in such a situation. If that's not practical, it might be better to use FAT or HFS (not HFS+) for data exchange.

---

### Post by maszy on 2010-10-18
Many many thanks now it works.
I'm using HFS not HFS+.

Greeting 
Massimiliano

---

### Post by srs5694 on 2010-10-18
I'm glad it worked, but I doubt if you're using HFS, since the procedure I outlined will only work with HFS+. To be sure, mount the disk and type this:

```

grep hfs /etc/mtab

```If the resulting line reads "hfs", then it's HFS; if it reads "hfsplus", then it's HFS+. If you've got more than one HFS or HFS+ partition mounted, you'll get multiple lines of output.

Edit: Oh, I should mention: Most Apple tools refer to HFS+ as "Mac OS Extended". The names can be a bit confusing.

---

