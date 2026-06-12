---
title: "Help! Trying to recover from HD crash"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by Razmear on 2009-10-10
OK, my system was setup with Grub on my 'C' drive which pointed to my 'E' drive for my Ubuntu system. 
My C drive was about dead, but held the Grub bootloader and worked well enough to get me to my E drive and run Ubuntu happily for almost a year. 
Today after a reboot the C: drive started knocking and finally died. 
I have removed the C: drive, moved E to the master slot on the first IDE controler, and am currently only able to boot Ubuntu using the Live CD in "Try before you install" mode. (which is how I'm typing here)

Choosing the option to Boot from First Hard Disk just says Booting... forever. 
I tried to run Install but it displayed nothing on the drive partition screen. 
I have no way to access any local drives while in "Try before" mode. 

Can anyone offer some assistance in getting my system back up and running? 
I do not want to loose the contents of my Home directory as it has my mail stores and everything else. I'm using EXT3 on the C: drive, the D: drive is NTFS and has all my media files so they are safe. 
I think all I need to do is get Grub installed on the boot drive, but having no access in Try Before mode I don't know how I'd do that. 

I guess if I was smart enough to have done a backup of my home directory I wouldn't be in this mess, but here I am. 

Thanks for any help you can offer,
eb

---

### Post by Hukei on 2009-10-10
Perhaps, as you say, you just need to re-install the boot loader, Grub. You may want to visit [this thread]("http://ubuntuforums.org/showthread.php?t=224351"). Follow the steps and let me know.

By the way, if you could attach some screenshots it would be useful.

---

### Post by Razmear on 2009-10-11
Thanks for the pointer to the thread. 

Getting this error: 

grub> find /boot/grub/stage1

Error 15: File not found

grub> 

Not looking good....

eb

Edit:
sudo fdisk -l | grep -i linux
returns no results either. 
So it's either the install disk in Try mode can't see the hard drives for obvious security reasons, wouldn't want anyone with a LiveCD being able to bypass your password, right? 
Or the drives don't exist/work anymore.
Or I need a way to mount the drives before any of this will work. 
Sorry rambling a bit....

eb

---

### Post by Hukei on 2009-10-11
Try the other method below that one, I guess that would help.

---

### Post by kansasnoob on 2009-10-11
Post the output from terminal of:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by Razmear on 2009-10-11
Working on getting the screenshot posted. will edit

Basically popped up the gui app which reported in the status bar No Devices Detected and stayed blank

Also ran mount -l and got this output: 
```

ubuntu@ubuntu:~$ mount -l
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime) [Ubuntu 9.04 i386]
/dev/loop0 on /rofs type squashfs (ro,noatime) []
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

I'm running man mount now to see how to mount the other drives. I think it has to do with the LiveCD environment.

eb

Contents of /etc/fstab
```

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

---

### Post by Hukei on 2009-10-11
Did you make sure your BIOS detected correctly the Hard Disk Drive? Also, did you changed the jumper settings to Master (if not Cable Select) when changing it to the first slot of IDE? If the Hard Disk was detected earlier, there should have been some problem when changing it from the slot.

---

### Post by Razmear on 2009-10-11
Yeah, I'm thinking hardware issue too, gonna shut down and recheck the cables/bios/jumpers and so forth. This HP case is a pita to work inside of. 

eb

---

### Post by kansasnoob on 2009-10-11
The output of:

```
sudo fdisk -l
``` 

would show us how Ubuntu recognizes the drive and partitions.

---

### Post by Razmear on 2009-10-11
Allrighty, I went back into the case, pulled the drives out, checked everything and put em all back in and now I can see my drives again. YaY.

Now to get Grub installed and I should be good to go (fingers crossed). 

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35093509

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe989200b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

I'm feeling much better now....
eb

---

### Post by Hukei on 2009-10-11
If anything arises again, don't hesitate to leave a message!

---

### Post by kansasnoob on 2009-10-11
> **Razmear said:**
> Allrighty, I went back into the case, pulled the drives out, checked everything and put em all back in and now I can see my drives again. YaY.

Now to get Grub installed and I should be good to go (fingers crossed). 

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35093509

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe989200b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

I'm feeling much better now....
eb

This is not hard at all give me a few minutes to type everything and double check it.

I'll be right back.

---

### Post by Razmear on 2009-10-11
YaY,
I'm back in. 
Booting fine with the old C drive removed thanks to the thread link Hukei posted and using the Grub command line interface. 

Thanks for all the support!
eb

---

### Post by kansasnoob on 2009-10-11
First we need to mount and chroot sda1 which is your Ubuntu root (/) partition, and physically install grub to sda, so copy-n-paste the following commands:

```
sudo mount /dev/sda1 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

```
sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev
```

```
sudo umount /mnt/proc
```

```
sudo umount /mnt
```

Now we need to setup grub so follow these commands:

```
sudo grub
```

```
root (hd0,0)
```

```
setup (hd0)
```

If correct you should see an output like:
&#65279;
> Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done. 

If it fails it'll tell you so! If it succeeded just type (or copy-n-paste):

```
quit
```

You should be good to go!

---

### Post by Razmear on 2009-10-11
Thanks for the writeup Kansas,
Actually all I needed to do was from sudo grub onwards to get it working, but the rest is educational towards my total lack of command line knowledge. 

eb

---

### Post by kansasnoob on 2009-10-11
Cool!

---

