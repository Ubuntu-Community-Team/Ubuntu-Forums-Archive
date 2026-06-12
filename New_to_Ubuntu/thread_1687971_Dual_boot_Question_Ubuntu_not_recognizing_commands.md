---
title: "Dual boot Question Ubuntu not recognizing commands"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by C.Clear on 2011-02-14
So I'm a newbie and i was trying to set up a windows xp/ubuntu 10.10 dual boot. I followed these directions here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

And unfortunately due to my error or something else I cannot reinstall Grub into the MBR.

This is a copy of what i did and the error message I got

ubuntu@ubuntu:~$  mount | tail -1
/dev/sda3 on /media/cdd15088-bf7e-4330-bafc-4c4860be5788 type ext4 (rw,nosuid,nodev,uhelper=udisks)
ubuntu@ubuntu:~$ ls /media/cdd15088-bf7e-4330-bafc-4c4860be5788/boot
abi-2.6.35-22-generic     config-2.6.35-25-generic      initrd.img-2.6.35-25-generic  System.map-2.6.35-22-generic  vmcoreinfo-2.6.35-25-generic
abi-2.6.35-25-generic     grub                          memtest86+.bin                System.map-2.6.35-25-generic  vmlinuz-2.6.35-22-generic
config-2.6.35-22-generic  initrd.img-2.6.35-22-generic  memtest86+_multiboot.bin      vmcoreinfo-2.6.35-22-generic  vmlinuz-2.6.35-25-generic
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/cdd15088-bf7e-4330-bafc-4c4860be5788/dev/sda3
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.
ubuntu@ubuntu:~$ 



Any suggestions as to how I may fix this problem ??

---

### Post by matt_symes on 2011-02-14
HI

```
sudo grub-install --root-directory=/media/cdd15088-bf7e-4330-bafc-4c4860be5788/dev/sda3
```

Try this instead

```
sudo grub-install --root-directory=**/media/cdd15088-bf7e-4330-bafc-4c4860be5788** **/dev/sda3**
```

Notice the extra space ?

Kind regards

---

### Post by C.Clear on 2011-02-14
> **matt_symes said:**
> HI

```
sudo grub-install --root-directory=/media/cdd15088-bf7e-4330-bafc-4c4860be5788/dev/sda3
```Try this instead

```
sudo grub-install --root-directory=**/media/cdd15088-bf7e-4330-bafc-4c4860be5788** **/dev/sda3**
```Notice the extra space ?

Kind regards

Thank you very much for the suggestion. Ran the command with the extra space but still got a error message this time the message was:

[B]ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/cdd15088-bf7e-4330-bafc-4c4860be5788 /dev/sda3
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$ [/B]

Not sure if I should use the force command they suggest or not?

---

### Post by matt_symes on 2011-02-14
Hi

> ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/cdd15088-bf7e-4330-bafc-4c4860be5788 /dev/sda3
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$ 

You want to install grub into the MBR of the disk and not the partition. You can 'use the force' if you want to force install on the partition but, as the warning says, the MBR is the general location to install GRUB.

What exactly are you trying to do ?

Kind regards

---

### Post by C.Clear on 2011-02-14
> **matt_symes said:**
> Hi



You want to install grub into the MBR of the disk and not the partition. You can 'use the force' if you want to force install on the partition but, as the warning says, the MBR is the general location to install GRUB.

What exactly are you trying to do ?

Kind regards

Well  I ahd to reinstall Windows XP and trying to alter the MBR so that I can boot into Ubuntu which I currently can't. How would I find out which partition  the MBR is located

Gparted has the boot listed as sda1 which is my windows partition. should I run these commands from there ??

---

### Post by matt_symes on 2011-02-14
Hi

From the LiveCD open a terminal and type

```
sudo fdisk -l
```

That is a small L above. Also enter this

```
mount | grep ^/
```

and this

```
sudo blkid
```

Post the results back here.

Kind regards

---

### Post by C.Clear on 2011-02-14
> **matt_symes said:**
> Hi

From the LiveCD open a terminal and type

```
sudo fdisk -l
```That is a small L above. Also enter this

```
mount | grep ^/
```and this

```
sudo blkid
```Post the results back here.

Kind regards

Followed your instructions here are the results:

[B]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
240 heads, 63 sectors/track, 10637 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc8c8c8c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1693    12799048+   7  HPFS/NTFS
/dev/sda2            1694        3048    10233405    7  HPFS/NTFS
/dev/sda3            3048       10096    53283840   83  Linux
/dev/sda4           10096       10638     4094977    5  Extended
/dev/sda5           10096       10638     4094976   82  Linux swap / Solaris
ubuntu@ubuntu:~$ mount | grep ^/
/dev/sr2 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/dev/sda3 on /media/cdd15088-bf7e-4330-bafc-4c4860be5788 type ext4 (rw,nosuid,nodev,uhelper=udisks)
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="C08886A888869D12" TYPE="ntfs" 
/dev/sda2: UUID="7A4F6CAF7B66A8A5" TYPE="ntfs" 
/dev/sda3: UUID="cdd15088-bf7e-4330-bafc-4c4860be5788" TYPE="ext4" 
/dev/sda5: UUID="c6897f57-41fc-4c9f-82e7-2557a8eda0d5" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
ubuntu@ubuntu:~$ 

[/B] Just wanted to thank you so much for your help up to this point. Despite the fact that I have not got it sorted I'm making the most progress I've had all day.

---

### Post by drs305 on 2011-02-14
If you have both Windows and Ubuntu installed, and Ubuntu is on sda3 and you want to use Grub2 as the bootloader:

Boot a LiveCD.
Mount the Ubuntu partition (I'm assuming it is the one quoted) then just install to the MBR *without designating a partition in the third command*:

```

sudo umount /dev/sda3  # Added to ensure sda3 isn't mounted elsewhere
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by C.Clear on 2011-02-14
> **drs305 said:**
> If you have both Windows and Ubuntu installed, and Ubuntu is on sda3 and you want to use Grub2 as the bootloader:

Boot a LiveCD.
Mount the Ubuntu partition (I'm assuming it is the one quoted) then just install to the MBR *without designating a partition in the second command*:

```

sudo umount /dev/sda3  # Added to ensure sda3 isn't mounted elsewhere
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```


I believe I've had success; Made a erro on the sudo grub-install --root-directory=/mnt /dev/sda line by changing it to sda3: 

[B]ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda3
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
[/B]

Recopied  it exactly as you typed it and got this:

[B]ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
mount: /dev/sda3 already mounted or /mnt busy
mount: according to mtab, /dev/sda3 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.[/B]

Hope I'm sorted. Thank you so much for your assistance.

---

### Post by C.Clear on 2011-02-14
> **C.Clear said:**
> I believe I've had success; Made a erro on the sudo grub-install --root-directory=/mnt /dev/sda line by changing it to sda3: 

[B]ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda3
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
[/B]

Recopied  it exactly as you typed it and got this:

[B]ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
mount: /dev/sda3 already mounted or /mnt busy
mount: according to mtab, /dev/sda3 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.[/B]

Hope I'm sorted. Thank you so much for your assistance.

Got it!! Thanks so much for your assistance, and pardon the bad spelling. Have a great week !

---

### Post by drs305 on 2011-02-14
> **C.Clear said:**
> Got it!! Thanks so much for your assistance, and pardon the bad spelling. Have a great week !

:-)

If it boots Ubuntu but you don't see a Windows menu entry, run the following:

```
sudo update-grub
```
That should find Windows and add it to the menu if Grub2 didn't find it the first time.

If everything is working properly, and you consider the thread SOLVED, please mark it so using the "Thread Tools" link at the top right of the first post.

Happy Ubuntu-ing!

---

