---
title: "Automount 2nd HD"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by wprecht on 2010-11-21
Hi,

I have a Dell m6400 with two HDs.  The first drive dual boots Win7 and Ubuntu 10.10 with a 50gb partition for Win7 and the rest for Linux.  I recently popped in a 250GB HD in the second HD bay and formated it ext4.  I am only using it for linux. Is there a way to get it to mount automatically at boot time rather than having to click on it in Nautilus?

Thanks in advance.

---

### Post by sikander3786 on 2010-11-21
Yes you can automount it but you'll need to define the mount paths in /etc/fstab.

Please post the output of

```
cat /etc/fstab
```

and

```
sudo blkid
```

Make sure that the external drive is plugged in when you do those commands ;-)

And note that if the external drive is not present when you boot Ubuntu, it might get stuck at the splash screen, waiting for you to press 'S' to skip mounting.

---

### Post by wprecht on 2010-11-21
This is s SATA internal HD in an internal drive bay, so luckily I can't forget to plug it or I probably would ;)

```

/dev/sda1: UUID="6E8E3C9D8E3C5FAF" TYPE="ntfs" 
/dev/sda5: UUID="4dc5ffd0-f295-4323-936d-876b12c59456" TYPE="ext4" 
/dev/sda6: UUID="1aa65a22-38a6-4baa-ad83-d12ae191f762" TYPE="swap" 
/dev/sdb1: LABEL="Drive_B" UUID="50a1315f-e3e3-4f36-bda0-75cbe4e9c681" TYPE="ext4"

```

---

### Post by sikander3786 on 2010-11-21
Edit you /etc/fstab by

```
gksudo gedit /etc/fstab
```

Place a new entry for sdb1. It would look like,

```
UUID=50a1315f-e3e3-4f36-bda0-75cbe4e9c681 /place/to/mount ext4 defaults 0 2
```

Replace /place/to/mount with your inteneded mount point.

You might need to chown that mount point to gain write access.

```
sudo chown username:username /place/to/mount
```

Replace username with your username and /place/to/mount with your mount point.

You didn't post the output for cat /etc/fstab so I don't know if it is somehow already defined there (??).

Good Luck!

---

### Post by wprecht on 2010-11-21
Whoops, sorry, here is the fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=4dc5ffd0-f295-4323-936d-876b12c59456 /               ext4    errors=remount-ro 0       1
UUID=1aa65a22-38a6-4baa-ad83-d12ae191f762 none            swap    sw              0       0

```

---

### Post by sikander3786 on 2010-11-21
> **wprecht said:**
> Whoops, sorry, here is the fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=4dc5ffd0-f295-4323-936d-876b12c59456 /               ext4    errors=remount-ro 0       1
UUID=1aa65a22-38a6-4baa-ad83-d12ae191f762 none            swap    sw              0       0

```
Ok thanks. No mount points defined for sdb. You can safely follow the procedure in post # 4.

---

### Post by wprecht on 2010-11-21
Thankssikander3786, that worked perfectly.**

---

