---
title: "New variation on &quot;Cannot Mount USB Device&quot;."
date: 2008-12-27
forum: New to Ubuntu
---

### Post by cobrajeep on 2008-12-27
I just upgraded to Xubuntu 8.10, and now anything I plug into my usb port gets recognized but not mounted.
I have read every version of "cannot mount USB device", "cannot mount memory stick", "cannot mount external hard drive"... where my problem differs is that it says "Problem Unknown", and all checks bring no result.
Any ideas?

---

### Post by taurus on 2008-12-27
See if you can mount it by hand from a terminal.  Post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by cobrajeep on 2008-12-27
It says:

```
sudo: fdisk -l: command not found
```

---

### Post by taurus on 2008-12-27
What about 

```
ls -la /sbin/fdisk
```

---

### Post by cobrajeep on 2008-12-28
Now it says:

```
-rwxr-xr-x 1 root root 73968 Oct 22  2007 /sbin/fdisk

```

I have *no idea* what that means, or what the last bit of code you passed me was.

---

### Post by taurus on 2008-12-28
It means /sbin is not in your path so when you run fdisk, system didn't even bother to look in /sbin.  As a result, you would get that error message about command not found.

Now, you just have to include the whole path, or complete path.

```
sudo /sbin/fdisk -l
```

---

### Post by cobrajeep on 2008-12-28
OK- now it tells me that
```

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4795    38515806   83  Linux
/dev/hda2            4796        4864      554242+   5  Extended
/dev/hda5            4796        4864      554211   82  Linux swap / Solaris

Disk /dev/sda: 2055 MB, 2055207936 bytes
33 heads, 63 sectors/track, 1930 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1931     2007023    b  W95 FAT32

```

---

### Post by taurus on 2008-12-28
See if you can mount it from a terminal with

```
sudo mkdir /media/sda1
sudo mount -t vfat /dev/sda1 /media/sda1 -o umask=000
df -h
```

---

### Post by cobrajeep on 2008-12-28
That worked! Thank you!

---

### Post by cobrajeep on 2008-12-28
Oh, for the sake of form:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              37G   11G   25G  30% /
varrun                 93M  100K   93M   1% /var/run
varlock                93M  4.0K   93M   1% /var/lock
udev                   93M   88K   93M   1% /dev
devshm                 93M     0   93M   0% /dev/shm
lrm                    93M   19M   75M  20% /lib/modules/2.6.15-52-386/volatile
/dev/hdc              173M  173M     0 100% /media/cdrom0
/dev/sda1             2.0G  334M  1.6G  18% /media/sda1

```

---

### Post by cobrajeep on 2008-12-31
So, is there anything I can do in order to not have to do this every time I want to mount or eject a flash drive?

---

