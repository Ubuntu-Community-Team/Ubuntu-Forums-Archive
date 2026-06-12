---
title: "Grub error : unknown filesystem"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by ravipatel_ce on 2011-08-07
Hi, i have installed Ubuntu 10.04 and Windows 7 was already installed.  But after installing Ubuntu, windows was not booting properly. So, i  decided to uninstall both and reinstall windows7. I deleted all  partitions, created new partition table and started installing windows7.  But installation gave error, so i tried windows xp and it was also not  getting installed.

 I tried to install ubuntu 11.04 but it was giving following error:
(initramfs) Can not mount /dev/loop0(/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

When i try to boot,
 the grub error is displayed as follows:
error: unknown filesystem.
grub rescue>

So,  i  am stuckup now, i dont have any os on my pc and can not install any  os on my pc. If any one have faced this kind of problem then please help  me. Thanks in advance.

---

### Post by Basher101 on 2011-08-07
Have you created the partitions needed by the OSs? NTFS for windows and ext4 for linux. Try setting them up with Gparted from the Ubuntu Live CD

---

### Post by ravipatel_ce on 2011-08-07
Thanks for replaying basher101,

Yes, i used Gparted and i created  new partition table with one partition having ntfs file system(50 gb)  and one partition having ext3(50gb). After that i tried to install  ubuntu 11.04 from usb using UNetbootin. But i am getting following  error:

Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesysstem.squashfs

I also tried to install windows and i get following error': 

'There is no disk in the drive. Please insert a disk into drive D:'.

I have no idea what is happening with my machine.

---

### Post by amjjawad on 2011-08-07
Here is what you need to do:

1- If your machine is 32bit, make sure your Ubuntu is 32bit too. Otherwise, it doesn't matter if you have 64bit machine as both will work (unless you have 4GB RAM or more - you need 64bit).

2- Your download might be damaged so you need to check MD5SUM. Here is how: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
That link will help you.

3- Make sure you are creating a bootable LiveCD or LiveUSB.

a- If you're creating LiveCD, make sure to burn it with the lowest possible speed. I always use 8x and I have no issues whatsoever.

b- If you're creating LiveUSB, make sure to follow the correct steps.

On Ubuntu website -download page, there is a HOWTO Create both LiveCD and LiveUSB.

4- Boot your machine from Ubuntu LiveCD or LiveUSB

5- Run GParted

6- Follow this: [http://ubuntuforums.org/showpost.php?p=11101707&postcount=129](http://ubuntuforums.org/showpost.php?p=11101707&postcount=129)

7- Try now to install Windows then Ubuntu.


If you need any help, please let us know.

---

### Post by ravipatel_ce on 2011-08-26
Problem solved...
my ubuntu 11.04 image was currupted and checksum was not matching.
Thanks for your valueable replies guys.

---

### Post by amjjawad on 2011-08-27
> **ravipatel_ce said:**
> Problem solved...
my ubuntu 11.04 image was currupted and checksum was not matching.
Thanks for your valueable replies guys.

Glad to know that ;)

Please mark this thread as SOLVED

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

