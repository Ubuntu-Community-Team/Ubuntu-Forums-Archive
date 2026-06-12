---
title: "Permission denied"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by St Nabi on 2010-08-09
Hi there, 

Since I upgraded to 10.04, I can't seem to carry out tasks as it says permission denied check settings.

I am stuck. 

eg, can't even move files from desktop to external hard drive as before as permission is denied.

Do not know what to do.

Regards

St Nabi

---

### Post by Ozymandias_117 on 2010-08-09
How is your external hard drive formatted?

---

### Post by St Nabi on 2010-08-09
Sorry not sure what you mean, it was all working perfectly well before

---

### Post by Ozymandias_117 on 2010-08-09
Can you post the output of ```
fdisk -l
``` please. (With the hard drive attached)

---

### Post by St Nabi on 2010-08-09
No idea how to do that, sorry...

---

### Post by Finalfantasykid on 2010-08-09
Go to the terminal:

Applications > Accessories > Terminal

And then enter in exactly what he posted, then press enter

---

### Post by St Nabi on 2010-08-09
nothing happened ...

---

### Post by Ozymandias_117 on 2010-08-09
> **St Nabi said:**
> nothing happened ...

My bad. Forgot to tell you to sudo it.```
sudo fdisk -l
``` (That is a lowercase L, not the number one)

---

### Post by St Nabi on 2010-08-09
Disk /dev/sda: 250.0 GB, 250000000000 bytes 255 heads, 63 sectors/track, 30394 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x00000001     Device Boot      Start         End      Blocks   Id  System /dev/sda1   *           1       27007   216933696    7  HPFS/NTFS /dev/sda2           27008       30394    27206077+   5  Extended /dev/sda5           27008       30248    26033301   83  Linux /dev/sda6           30249       30394     1172713+  82  Linux swap / Solaris  Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes 255 heads, 63 sectors/track, 121601 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0xe8900690     Device Boot      Start         End      Blocks   Id  System /dev/sdg1               1      121601   976760001    c  W95 FAT32 (LBA)

---

### Post by Ozymandias_117 on 2010-08-09
Could you please post the output of ```
mount
``` Also, at the top of the new post window, there should be an icon there that looks like this: # Press that and then paste the output between the two blocks that button added.

---

### Post by St Nabi on 2010-08-09
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro) proc on /proc type proc (rw) none on /sys type sysfs (rw,noexec,nosuid,nodev) none on /sys/fs/fuse/connections type fusectl (rw) none on /sys/kernel/debug type debugfs (rw) none on /sys/kernel/security type securityfs (rw) none on /dev type devtmpfs (rw,mode=0755) none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) none on /dev/shm type tmpfs (rw,nosuid,nodev) none on /var/run type tmpfs (rw,nosuid,mode=0755) none on /var/lock type tmpfs (rw,noexec,nosuid,nodev) none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755) /dev/sdg1 on /media/usb0 type vfat (rw,noexec,nodev,sync,noatime,nodiratime) binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) gvfs-fuse-daemon on /home/stnabi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stnabi)

---

### Post by Ozymandias_117 on 2010-08-09
What is in ```
cat /etc/fstab
```

---

### Post by St Nabi on 2010-08-09
# /etc/fstab: static file system information. # # Use 'vol_id --uuid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # #                 proc            /proc           proc    defaults        0       0 # / was on /dev/sda5 during installation UUID=c78caa16-e701-4dae-84fd-353a42aeace5 /               ext3    relatime,errors=remount-ro 0       1 # swap was on /dev/sda6 during installation UUID=381379ae-4ea3-4876-baaf-b4e258b8bbbb none            swap    sw              0       0

---

### Post by Ozymandias_117 on 2010-08-09
The problem is with the mount options. I'm not sure why it's getting mounted with the options you've posted. Hopefully someone more knowledgeable than I am will come along and help you fix the underlying problem.

Here is a temporary fix though.

```

sudo umount /dev/sdg1
sudo mkdir /media/flashmnt
sudo mount -t vfat -o rw,nosuid,nodev,uid=1000,gid=1000 /dev/sdg1 /media/flashmnt
```

You will have an icon on your desktop for your drive, and you should be able to read/write to it.

Edit: Note that if you use this again in the future, you can omit the second command (sudo mkdir /media/flashmnt)

---

### Post by St Nabi on 2010-08-09
Thanks.   I will try it and let you know later on.  Cheers St Nabi

---

