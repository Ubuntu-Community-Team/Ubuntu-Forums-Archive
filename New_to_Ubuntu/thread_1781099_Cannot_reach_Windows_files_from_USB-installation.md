---
title: "Cannot reach Windows files from USB-installation"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by yc2 on 2011-06-13
Hi,

I run 11.04 on a USB stick (Acer netbook D255E) installed according to ubuntu.com/pendrivelinux instructions. It works fine, but I can't reach the Windows files on the HDD. As I remember and guess, I could reach them the first time I tried, but now it is not possible since the graphic interface in Ubuntu is trying to mount the Win partition even though it is already mounted??? (Win 7 starter)

This is what I get when I click the partition "Acer" (Windows).

I close Windows every time I leave it, I do NOT hibernate it.

```
Error mounting: mount exited with exit code 16: Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
```

I dont know how to find the Acer (Win) partition. Therefore I cant use fuser command. It is not in /media or /mnt. This is what I get with mount.

```
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /dev type devtmpfs (rw,relatime,size=1017956k,nr_inodes=214711,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/dev/loop1 on /cow type ext2 (rw,noatime,errors=continue)
aufs on / type aufs (rw,noatime,si=41a93462)
none on /sys/kernel/debug type debugfs (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,relatime,user_id=999,group_id=999)

```

Grateful for advice.

Thanks

ycc

---

### Post by manzdagratiano on 2011-06-13
Can you try adding the following line to /etc/fstab? (Assuming your Windows partition is /dev/sda1 - please change it accordingly. You will also have to create the mounting folder in /media or wherever you wish by issuing an 'mkdir' - I am calling it 'windows')

```

/dev/sda1 /media/windows ntfs-3g defaults,user 0 2

```

After that, reboot and see if the windows drive is mounted when Gnome fires up. If it is not, then we can try looking at the output of:

```

$ sudo mount -a

```

and see what's wrong.

---

### Post by yc2 on 2011-06-13
Thanks, good idea, but I think something bad happened, due to what I did or not?

I can no longer access the internet (hotel wifi) from Ubuntu. My impression is that it is a DNS error, I can ping the few IPs I remember, but not DNS-named domains.

I have no access to the router and I cant find how to only change DNS servers, and I am not allowed static IP.

Running from Win now, cant access Internet from ubuntu. (Connection and signal is OK)

I tried to do what you suggested. fstab is very different from the traditional, but I added my Win partition (sda4) using
gksu gedit /etc/fstab

I made backup of fstab, but it is the same as the one I edited. When I now check the situation, it seems I got error messages after editing fstab. It never got written properly. Sorry, cant dplicate error messages, cant access internet from ubuntu.

I tried manually mounting windows in /media but got same error as from before.

Grateful for advice how to get back Internet and then we will try to solve original problem.

Thanks

---

### Post by yc2 on 2011-06-13
I reformat the USB stick now and put a new 11.04/pendrivelinux on it.

---

### Post by yc2 on 2011-06-13
The new stick works. If I click the Windows partition I can see the files. If I restart the computer with or without first unmounting the Windows partition it still works. I dont know what happened last time but now its ok. Keep our fingers crossed ;)

---

