---
title: "grub not installed during boot"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by pjo123 on 2009-06-12
Hi all.

Dual boot windows 7 and ubuntu, ubuntu installed onto spare hd

Started installation, under the partitioning told it to use the entire spare hd (sdc)

Install started, said it was formatting, stayed for literally ages at 5%, went out shopping, came back to find myself in a live session.  If I reboot, it boots into windows.

The linux partition (sdc) has been automatically mounted in the live session as /target.

/dev/sda1 is ntfs system reserved
/dev/sda2 is windows 7
/dev/sda3 is a ntfs data partiton for windows

/dev/sdb1 is another ntfs data partition for windows
/dev/sdb2 is yet another ntfs data partition for windows

/dev/sdc3 is ext3 mounted as /target
/dev/sdc2 is extended
/dev/sdc5 is linux swap

looking at fstab on /target/etc/fstab it shows

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=e67a6d89-6263-47ae-b795-e60c5a78e036 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=5cad4f53-8910-43b6-9736-bf9d16395c34 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


in /target/boot I have the following

-rw-r--r-- 1 root root  525592 2009-04-17 03:34 abi-2.6.28-11-generic
-rw-r--r-- 1 root root   90584 2009-04-17 03:34 config-2.6.28-11-generic
drwxr-xr-x 2 root root    4096 2009-06-12 18:43 grub
-rw-r--r-- 1 root root  128796 2009-03-27 20:12 memtest86+.bin
-rw-r--r-- 1 root root 1871601 2009-04-17 03:34 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root    1170 2009-04-17 03:39 vmcoreinfo-2.6.28-11-generic

in /target/boot/grub I have 1 file, called device.map, this contains

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

please can someone advise/point me into the right direction on how I set up grub properly?

many thanks

---

### Post by juanoleso on 2009-06-12
Hi, I had a similar problem recently.

To start, I would see if you can't use supergrubdisk to boot into that ubuntu partition.

Either way, from the live disk or the HD boot, make sure grub is installed (which it most likely is).  Then run grub-install with your /dev/sdc3 (linux ext3 partition) as a parameter.  Then run update-grub.  Then go into the grub console.  Find which hd grub thinks your stage1 file is on.  set that as the root and then run the setup on the hd you are booting from to install onto the MBR.  here it is all coded out.

```

tty1093vm~$ sudo -i

Password:

tty1093vm:/home/noleson# aptitude install grub -y

tty1093vm:/home/noleson# grub-install /dev/hda1

Searching for GRUB installation directory ... found: /boot/grub
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/hda

tty1093vm:/home/noleson# update-grub

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.26-2-686
Updating /boot/grub/menu.lst ... done

```

That will get you your grub folder.  Now the rest is coming off of the ubuntu grub wiki here, [[COLOR="Blue"]https://help.ubuntu.com/community/GrubHowto[/COLOR]]("https://help.ubuntu.com/community/GrubHowto").  If you have trouble after here, then you should refer back to that wiki page.

```

tty1093vm:/home/noleson# grub

grub> find /target/boot/grub/stage1
 (hd0,0)

```

Then take that and give it to a root command as such:

```


grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

```

The next command sets up the MBR, so this needs to be set to whatever HDD your bios is set to boot on, which is probably your windows?

```


grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> quit


```

If grub did everything right, then you should be good to go.  If you reboot and get an error then grub might not have picked out the right hd to boot.  Try editing the lines in the grub menu until you find the right hd and then when you boot up, fix your menu.lst.  I hope I was clear enough.

---

### Post by jbrown96 on 2009-06-12
1) Boot the live CD and then use fdisk to make sure that /dev/sda /dev/sdb remained constant (i.e. your installation is /dev/sdc). 
2) Install grub to sdc ```
sudo grub-install /dev/sdc
``` This should take care of the installation. 
3) Change /boot/grub/menu.lst on /dev/sdc
you will find your entries at the bottom and something like > hd(0,0) where the 0's could be anything. You will want to change it to > hd(2,2) You can edit this file with gedit. 
4) You will probably want to include listings for Windows on there as well. There is a sample somewhere in the menu.lst file. copy and paste that at the bottom and remove the # signs at the beginning of each line (anything that begins with # is ignored). You will want to change the hd(0,0) part to hd(0,1). You can also change the order of each listing. There is also a default option at the top of the file, so if you want Windows to boot by default and just use Ubuntu sometimes that can be done. Beware that anything with a "title" line is an entry, and it starts counting at 0. For example,

title Ubuntu 9.04 ...
kernel ...

titile Ubuntu 9.04 Rescue
kernel ...

title Other Operating Systems

title Windows 7

To make Windows the default change the default from 0 to 3. 

you will also need to change your BIOS to have it boot from /dev/sdc, so it doesn't automatically read from /dev/sda and always boot windows

---

### Post by pjo123 on 2009-06-13
Many many thanks for your responses.

Still wouldn't work, so I retried the install.

Turned out it hadn't simply gone to a live session, the install had failed due to hard drive problems (was a suspect one out of my sky HD box), must have cleared the error message on the original install when I touched the keyboard to get the monitor out of power save mode.

Sorry for your wasted time (but very useful info all the same)

Have a spare smaller drive that  know is fine, will re-do the install using that

thanks again

---

