---
title: "mkfs.netf refuses to create filesystem on file"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-05-30
Question: I can create a vfat filesystem as shown below.
I can exchange mkfs.vfat with mkfs.jfs or mkfs.ext3, but when I exchange it with mkfs.ntfs, then I get this error message:
virtual.dsk is not a block device.
Refusing to make a filesystem here!

Is there a way/cmd line option to create an nfts fs from a file ?

```

Create a virtual disk
dd if=/dev/zero of=virtual.dsk bs=1048576 count=150


Format it
mkfs.vfat virtual.dsk


Mount it
sudo mkdir -p /mnt/vfat
sudo mount virtual.dsk /mnt/vfat -t vfat -o loop

```

---

### Post by Eisenwinter on 2010-05-30
Where is virtual.dsk located? You may need to specify the entire path, for example:

```
mkfs.ntfs /dev/virtual.dsk
```

---

### Post by WitchCraft on 2010-05-30
> **Eisenwinter said:**
> Where is virtual.dsk located? You may need to specify the entire path, for example:

```
mkfs.ntfs /dev/virtual.dsk
```

It's location: /tmp/virtual.dsk

Upon your question, I moved it to /dev and tried again, but no success. It's still disallowed to create a ntfs there because it is not a block device..

---

### Post by WitchCraft on 2010-05-30
Uh, never mind, the magic option is:
[http://ubuntu-rescue-remix.org/node/215](http://ubuntu-rescue-remix.org/node/215)


mkfs.ntfs -F filname.extension

Solved.

PS: Permanently mount:
/path/to/virtual.dsk /mnt/vfat vfat loop,owner,group,umask=000 0 0

use 
```

mount -a 

```
to 'reload' the /etc/fstab file.

---

### Post by WitchCraft on 2010-06-05
But why is the NTFS filesystem case-sensitive, while VFAT is not ?

---

### Post by WitchCraft on 2010-11-16
Bump.

---

### Post by WitchCraft on 2012-05-30
As a secret tip if anybody needs a case-insenstive file system:

FAT is covered by patents.
Therefore, use JFS with the -O option.

```

apt-get install jfsutils
dd if=/dev/zero of=jfs.dsk bs=1048576 count=150
mkfs.jfs -O jfs.dsk
mkdir -p /mnt/jfs
mount /volumes/jfs.dsk /mnt/jfs -t jfs -o loop
umount /mnt/jfs/

```

---

### Post by overdrank on 2012-05-30
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

