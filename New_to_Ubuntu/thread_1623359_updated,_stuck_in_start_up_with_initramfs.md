---
title: "updated, stuck in start up with initramfs"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by nyotok on 2010-11-16
Please excuse me, but I have no idea what to do from here. Any help is appreciated!
 
This is what my screen says:
 
udevadm trigger is not permitted while udev is unconfigured.a
Gave up while waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/05d7d0c8-b174-404b-b759-4271941d63ba does not exist. Dr opping to a shell!
 
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
(initramfs)

---

### Post by Hippytaff on 2010-11-16
Hi and welcome :-)

It will help people help you out if you can provide some info.

how is ubuntu installed (eg Wubi or 'real' install)?
How are you updating (eg update manager? disc install etc)
What version are you updating to and from (eg Maverick - 10.10 from Lucid - 10.04)
 and What are the specs of your pc?

:-D

---

### Post by deconstrained on 2010-11-16
Common problem. Most likely causes: grub didn't get properly configured, the initial ramdisk that gets loaded into memory at boot time wasn't properly built, or the build/configure process was interrupted. Here's what I'd try doing in this case:

1. Boot to a live disk
2. Open a terminal and start a superuser session with 'sudo -i'
3. Make a folder (we'll call it /mnt/root) with mkdir, mount your root partition there
4. Mount your boot in /mnt/root/boot
5. Mount the proc/dev filesystems; 'mount -o bind /dev /mnt/root/dev' and 'mount -t proc none /mnt/root/proc'
6. chroot into the folder; 'chroot /mnt/root'
7. Mount sys and pts; 'mount -t sysfs sys /sys', 'mount -t devpts devpts /dev/pts'
8. Fix your /etc/fstab; make sure that your boot partition, if any, has the same uuid as the one shown in /dev/disk/by-uuid/ (find out which is which with ls -l), and use "UUID=[uuid]" in the <file system> column of /etc/fstab, NOT "/dev/disk/by-uuid/[uuid]". 
9. Run 'update-initramfs -k all -c' and then [re-run grub with 'update-grub'](https://help.ubuntu.com/community/GrubHowto). Alternately you could try running "dpkg --configure linux-image-(whatever kernel version you have)-generic" and "dpkg --configure grub2"

Re-install as a last resort. Good luck!

---

### Post by HavarN on 2010-11-16
> **nyotok said:**
> ALERT! /dev/disk/by-uuid/05d7d0c8-b174-404b-b759-4271941d63ba does not exist. Dr opping to a shell!

I think this tells you what has happened. The disk which the uuid 05d7d0c8-b174-404b-b759-4271941d63ba is pointing to does not exists any more.

If you have been rearranging cables inside your computer, maybe you forgot to reattach one?

I am guessing some important partition is not found in /etc/fstab.

You could boot from the regular desktop CD, mount the partitions and try to fix the file etc/fstab which is found in the system partition on your hard-disk.

---

### Post by HarrisonNapper on 2010-11-16
Yeah, this would also be thrown if there's a new HDDID or for whatever reason the uuid of the HDD has changed.

When it drops to terminal, do
```
ls -a /dev/disk/by-uuid
```

and that will tell you which uuids are recognized.

---

### Post by Pkirkham on 2010-11-17
I have just installed ubuntu netbook 10.10 
133 updates were proposed which I installed. A Reboot button was presented the system won't boot with the same error:
udevadm trigger is not permitted while udev is unconfigured.

I do have a boot USB key all I need to know is what I have to fix.
Since the loader is apparently looking for a UUID it can't find does this mean the UUIDs are changed during the update process. Seems strange. The disk certainly wasn't physically changed and ther's only one.

---

### Post by Pkirkham on 2010-11-17
By the way I did check the contents of grub.cfg against the UUID of the volume containing the Ubuntu partition and they were the same.

Now the problem has gone away all on its own.

---

