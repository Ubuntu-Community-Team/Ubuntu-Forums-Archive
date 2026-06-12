---
title: "Ubuntu 10.04 not booting"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by tane2010 on 2010-11-05
Hi! I tried to find information about my problem but didn't find anything that works.
I have been sitting 2hours for searching information and this is my last hope to get my system up and running.

Yesterday ubuntu 10.04 started to act slowly (computer is always on) so I rebooted machine.
After bios, I get message "Invalid system disk..........."
It's familiar message for me from windows times.

How I could fix boot?

I thought my hard drive is broken but when starting from live-cd, I can mount system hard drive and disk utility shows that disk is healthy and has no errors.

I haven't installed any updates since last reboot (about week ago).

I have been running windows on virtualbox ose ( can't figure out why this should matter)

I have experience from windows times that this problem could been solved with fix mbr/boot, but how to do it with linux?

I thought I could move important files to external hard drive but live cd doesn't mount other disks (ext4 filesystems). It only mounts disk where operating system is.

Oh, and I don't have other operating systems installed on any drive.

I'd be very thankful for any help!

---

### Post by drs305 on 2010-11-05
tane2010,

Welcome to the Ubuntu forums.  :-)

You don't have a flash drive or CD inserted at boot do you? 

10.04 also has an app called Disk Utility that can check the basic health of your hard drive (System, Administration, Disk Utility). You might want to take a look at the Smart Data section on the right; on the left is an option to check the filesystem, which would probably be a good idea as well.

I'd recommend backing up important files in case your system fails. From the LiveCD you should be able to mount your Ubuntu install and copy files to a flash drive.

Boot a LiveCD, then open a terminal (Applications, Accessories, Terminal). Mount the Ubuntu partition. I'll assume it's sda1 since you say it's your only install. If not, mount the correct partition.
```

sudo mount /dev/sda1 /mnt
nautilus /mnt
```
These commands should open the file manager looking at your Ubuntu folders. If you attach a flash drive it should be located in /media.

Now, as to recovering your system, from the LiveCD, you can try to reinstall Grub. Assuming it is Grub2, and that you have already mounted your Ubuntu install via the previous command, run the following command to reinstall Grub2. Again this assumes sda1 is your Ubuntu installation:
```
sudo grub-install --root-directory=/mnt /dev/sda
```
Note you do not use the partition number in the last command.

If you are still having problems, please go to the following site and download and run the boot info script. Post the contents of RESULTS.txt here.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by tkoco on 2010-11-05
The other possibility could be that the MBR is hosed. Would re-installing GRUB fix that?

> **drs305 said:**
> tane2010,

Welcome to the Ubuntu forums.  :-)

You don't have a flash drive or CD inserted at boot do you? 

10.04 also has an app called Disk Utility that can check the basic health of your hard drive (System, Administration, Disk Utility). You might want to take a look at the Smart Data section on the right; on the left is an option to check the filesystem, which would probably be a good idea as well.

I'd recommend backing up important files in case your system fails. From the LiveCD you should be able to mount your Ubuntu install and copy files to a flash drive.

Boot a LiveCD, then open a terminal (Applications, Accessories, Terminal). Mount the Ubuntu partition. I'll assume it's sda1 since you say it's your only install. If not, mount the correct partition.
```

sudo mount /dev/sda1 /mnt
nautilus /mnt
```
These commands should open the file manager looking at your Ubuntu folders. If you attach a flash drive it should be located in /media.

Now, as to recovering your system, from the LiveCD, you can try to reinstall Grub. Assuming it is Grub2, and that you have already mounted your Ubuntu install via the previous command, run the following command to reinstall Grub2. Again this assumes sda1 is your Ubuntu installation:
```
sudo grub-install --root-directory=/mnt /dev/sda
```
Note you do not use the partition number in the last command.

If you are still having problems, please go to the following site and download and run the boot info script. Post the contents of RESULTS.txt here.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by drs305 on 2010-11-05
> **tkoco said:**
> The other possibility could be that the MBR is hosed. Would re-installing GRUB fix that?

Yes. Despite the command name, that is the primary thing that "grub-install" does. It creates a core.img file, places modules into /boot/grub, and writes to the MBR, among other things.  It does not generate a grub.cfg file or touch the /etc/grub.d folder's files.

---

### Post by tkoco on 2010-11-05
> **drs305 said:**
> Yes. Despite the command name, that is the primary thing that "grub-install" does. It creates a core.img file, places modules into /boot/grub, and writes to the MBR, among other things.  It does not generate a grub.cfg file or touch the /etc/grub.d folder's files.

Thank you. I wondered about that. Now I know.

---

