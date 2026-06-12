---
title: "Move files to another partition"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by Twittery on 2009-07-10
Hello there.  I had a thought of backing up my data on a new partition and so I created  10 GB partition . I was able to mount it but how do I move my files to that partition . I mean I am having trouble with the permissions and whenever I try to mount it via terminal I get the error 

''[SIZE=2]'mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab[/SIZE]'''

Any help is appreciated .

---

### Post by kpkeerthi on 2009-07-10
We can't tell unless you post what command you used.

In general, the mount command would be
```
sudo mount -t <filesystem> <device> <mount-point>
```

Example:
```

sudo mkdir -p /media/data
sudo mount -t auto /dev/sda1 /media/data

```

---

### Post by drs305 on 2009-07-10
Is this an ext3 partition? If you want to add it to fstab, make sure you own the mount point and change fstab:
```

sudo chown -R *yourusername:* */path/mountpoint*
sudo blkid  # to get UUID
gksudo gedit /etc/fstab

```
Add this line to fstab:
> 
UUID=putUUIDhere /path/mountpoint ext3 defaults,users 0 2

Example:
UUID=89789e78-i3987-768k-889 /media/storage ext3 defaults,users 0 2

To test:
```

sudo umount -a  # Unmount all devices, disregard "busy" messages
sudo mount -a   # Mount all devices in fstab. If no error messages, mounted correctly.

```

---

### Post by nothingspecial on 2009-07-10
Where did you mount it?

---

### Post by Twittery on 2009-07-10
> **kpkeerthi said:**
> We can't tell unless you post what command you used.

In general, the mount command would be
```
sudo mount -t <filesystem> <device> <mount-point>
```Example:
```

sudo mkdir -p /media/data
sudo mount -t auto /dev/sda1 /media/data

```

That did the trick and I was able to back up all my content . Thanks to all for such quick responses and enjoy your day .

---

