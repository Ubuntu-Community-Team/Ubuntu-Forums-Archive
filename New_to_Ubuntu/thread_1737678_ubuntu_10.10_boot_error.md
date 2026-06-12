---
title: "ubuntu 10.10 boot error"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by jaob99 on 2011-04-23
Hi, i am booting windows 7 and ubuntu and it was working fine untill a few days ago when i got a error (after a power fail) on booting ubuntu that said something like
```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg

```
 
the same happens in recorery mode. however my windows 7 boots normally.
 
i dont want to reinstall it because it has some important stuff on it, but i would reinstall it if a could backup my stuff.
 
 
i dont know what is wrong with it :confused:
thank you for helping
 
 
jaob99

---

### Post by Rubi1200 on 2011-04-23
Hi and welcome to the forums :-)

Is this a Wubi install of Ubuntu?

The best thing to do is the following so we can see what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by jaob99 on 2011-04-24
hi Rubi1200, 
thank you for helping, i download it and ran it in the terminal but it stoped half way through, this is the output...
```
Checking sda1 for information...
Checking sda2 for information...
Checking sda3 for information...
Checking sda5 for information...
```
then it got stuck at sda5 and did not make the RESULTS.txt. so i left it... for a long time and nothing happend. so i think there is something wrong with my sda5 :(.
 
thanks
 
-Jaob99

---

### Post by grvsaxena419 on 2011-04-24
> **jaob99 said:**
> Hi, i am booting windows 7 and ubuntu and it was working fine untill a few days ago when i got a error (after a power fail) on booting ubuntu that said something like
```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg

```
 
the same happens in recorery mode. however my windows 7 boots normally.
 
i dont want to reinstall it because it has some important stuff on it, but i would reinstall it if a could backup my stuff.
 
 
i dont know what is wrong with it :confused:
thank you for helping
 
 
jaob99

Try booting using a live cd and then open a terminal and try
```
fsck -fy /dev/sdaX
```
X is the number of ubuntu partition.

---

### Post by Rubi1200 on 2011-04-24
> **jaob99 said:**
> hi Rubi1200, 
thank you for helping, i download it and ran it in the terminal but it stoped half way through, this is the output...
```
Checking sda1 for information...
Checking sda2 for information...
Checking sda3 for information...
Checking sda5 for information...
```then it got stuck at sda5 and did not make the RESULTS.txt. so i left it... for a long time and nothing happend. so i think there is something wrong with my sda5 :(.
 
thanks
 
-Jaob99
This could indicate a problem, but before you try anything else, this is what I would do.

Download and burn to CD, a Linux distro called Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

The advantage of Slax is that it doesn't try and auto-mount partitions, which is a problem if there is file-system damage.

Once booted with Slax, open a terminal and run the command for the script as before but with one exception; you do not need to preface the command with sudo since Slax uses a root terminal as default.

Post the results here and good luck.

---

### Post by jaob99 on 2011-04-24
Hi Rubi1200,
 
i booted the Slax CD but when I was booting it got this far
```
Marking TSC as unstable due to possible THC halt in C2
thermal LNXTHERM1:01: registered as thermal_zone0
ACPI: Thermal Zone [T201] (51 C)
lsapnp: Scanning for PnP cards...
lsapnp: No Plug & Play device found
```
(there was some code before it i just cant remember it)
then it stoped, so i wated for about 10 mins and nothing happend
i was just wondeing if it is suppost to do that or not.
 
thanks
 
-Jaob99

---

### Post by Rubi1200 on 2011-04-24
No, it should definitely not be doing that.

I am running out of ideas, but here is what you might try.

Boot the Ubuntu CD again, choosing to try not install.

Go to System > Administration > GParted

Once it opens, right-click on the swap partition and choose Swapoff.

Then, on your Ubuntu partition > select the option to Check.

Let it run and if there are errors, save the log and post it here.

---

### Post by jaob99 on 2011-04-24
hi Rubi1200,

should deactivating the swap take long. it says it is working but i dont think it is.

thank you for helping,
-Jaob99

---

### Post by Rubi1200 on 2011-04-24
It should only take a few seconds at most. I am going to ask some other users to jump in and offer suggestions.

Hang in there please.

---

### Post by coffeecat on 2011-04-24
> **jaob99 said:**
> ```
Checking sda1 for information...
Checking sda2 for information...
Checking sda3 for information...
Checking sda5 for information...
```then it got stuck at sda5 and did not make the RESULTS.txt. so i left it... for a long time and nothing happend. so i think there is something wrong with my sda5 :(.

Agreed. This is the one that needs checking first.

> **jaob99 said:**
> hi Rubi1200,

should deactivating the swap take long. it says it is working but i dont think it is.

I agree with Rubi1200. Disabling swap should take no more than a few seconds. Which is your swap partition? Is it sda5 by any chance? Or, if not, what filesystem is showing against sda5 in Gparted? Is there a big exclamation mark by sda5? 

If sda5 is not your swap partition, I don't believe it is necessary to swapoff before you check it. Try right-clicking on sda5 and choosing "check" as Rubi1200 suggested.

---

### Post by jaob99 on 2011-04-24
hi coffeecat,
 
sda5 is not my swap, sda6 is.
sda5 is my ubuntu partition.
 
there is not a big ! next to sda5.
in GParted the filesystem next to sda5 is "ext4".
 
i tryed checking sda5 but it just said it was pending and never did start :(.
 
thank you for helping me.
 
-Jaob99

---

### Post by coffeecat on 2011-04-24
> **jaob99 said:**
> i tryed checking sda5 but it just said it was pending and never did start :(.

You have to click on the green tick icon in the toolbar - it says "Apply all Operations" when you mouseover.

---

### Post by jaob99 on 2011-04-25
hello coffeecat,
i checked sda5 and this is the log i got;
 
```
 
GParted 0.6.2
Libparted 2.3
Check and repair file system (ext4) on /dev/sda5  00:00:00    ( ERROR )  
     calibrate /dev/sda5  00:00:00    ( SUCCESS )  
     path: /dev/sda5
start: 229255168
end: 309071871
size: 79816704 (38.06 GiB)  
 
check file system on /dev/sda5 for errors and (if possible) fix them  00:00:00    ( ERROR )  
     e2fsck -f -y -v /dev/sda5  
     Filesystem mounted or opened exclusively by another program?
 
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda5
 
 
 
 
========================================
 

```
 
thanks for helping
-Jaob99

---

### Post by coffeecat on 2011-04-25
> **jaob99 said:**
> [CODE]
     Filesystem mounted or opened exclusively by another program?

You cannot check the filesystem of a mounted partition. Was sda5 mounted? You need to boot up the live CD **and not mount anything from the Places menu**. Open Gparted and right-click on sda5. Is the "Unmount" option greyed out? If it isn't, click on "Unmount". If it is greyed out choose "check". Now click on the green "Apply" tick icon. Let us know what happens.

---

### Post by satanselbow on 2011-04-25
When you boot a livecd it will attempt to make use of existing linuxswap partitions on the internal harddrive...

This may then cause a problem repairing the disc in question.

When you boot the live CD use the "**noswap**" boot option ;)

---

### Post by coffeecat on 2011-04-25
> **satanselbow said:**
> When you boot a livecd it will attempt to make use of existing linuxswap partitions on the internal harddrive...

This may then cause a problem repairing the disc in question.

When you boot the live CD use the "**noswap**" boot option ;)

It's always useful to read the thread first. :wink:

> **Rubi1200 said:**
> 
Once it opens, right-click on the swap partition and choose Swapoff.


> **jaob99 said:**
> 
should deactivating the swap take long. it says it is working but i dont think it is.


> **Rubi1200 said:**
> It should only take a few seconds at most. I am  going to ask some other users to jump in and offer suggestions.

> **coffeecat said:**
> I agree with Rubi1200. Disabling swap should take no more than a few seconds. Which is your swap partition? Is it sda5 by any chance? Or, if not, what filesystem is showing against sda5 in Gparted? Is there a big exclamation mark by sda5? 

If sda5 is not your swap partition, I don't believe it is necessary to swapoff before you check it. Try right-clicking on sda5 and choosing "check" as Rubi1200 suggested.

I agree that disabling the swap partition would be ideal, but this is not going to interfere with doing a filesystem check on sda5, which is the immediate problem.

---

### Post by jaob99 on 2011-04-25
> **coffeecat said:**
> You cannot check the filesystem of a mounted partition. Was sda5 mounted? You need to boot up the live CD **and not mount anything from the Places menu**. Open Gparted and right-click on sda5. Is the "Unmount" option greyed out? If it isn't, click on "Unmount". If it is greyed out choose "check". Now click on the green "Apply" tick icon. Let us know what happens.
 
hello,
 
the unmount option is greyed out. when checking i got the same error :(.
 
thaks
-Jaob99

---

### Post by satanselbow on 2011-04-25
> **coffeecat said:**
> It's always useful to read the thread first. :wink:




Hmmm... nice... good luck... You obviously have the situation under control and am looking forward to a swift "solved" marker ;) You seem to be confusing number of beans with working knowledge.

---

### Post by coffeecat on 2011-04-25
> **jaob99 said:**
> hello,
 
the unmount option is greyed out. when checking i got the same error :(.
 
thaks
-Jaob99

That's frustrating.

Let's address  this swapoff issue. With a machine with a logical swap partition and a number of logical partitions, I can do a filesystem check using Gparted on an ext4 logical partition **without** disabling the swap partition which is in the same extended partition. Which is why I suggest that it is unnecessary for you to disable the swap partition before checking sda5.

However, something odd is going on with your system. When you tried to "swapoff" with Gparted, it hung on you - if I read you correctly. So something to do with the swap partition could conceivably be interfering with checking sda5. Let's go about it another way. Boot up the live CD, don't open Gparted yet and open a terminal. Run this command:

```
sudo swapoff -a
```Post any error message that you see - if any. When I do that, I get the terminal prompt within a second, which means it has completed successfully. Now open Gparted. Is the swap partition enabled or not? If not enabled, now try "check" on sda5 and see if that will now complete without error.

---

### Post by Rubi1200 on 2011-04-25
Turning swap off may not be the biggest problem right now. The fact that sda5 is throwing errors indicates file-system damage.

Try coffeecat's suggestion to turn swap off and then run this command and post the output for us please:

```
lsof | grep sda5
```This will hopefully tell us what process, identified by its PID, is holding the partition so we can kill it:

```
sudo kill <PID>
```If that is successful, then you should be able to run fsck from the terminal:

```
sudo e2fsck -f -y -v /dev/sda5
```

---

### Post by jaob99 on 2011-04-25
hi Rubi1200,
 
i ran the command, and ths is the output...
 
```
 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
 
ubuntu@ubuntu:~$ lsof | grep sda5
lsof: WARNING: can't stat() vfat file system /casper-rw-backing
      Output information may be incomplete.
lsof: WARNING: can't stat() ext2 file system /cow
      Output information may be incomplete.
jbd2/sda5   391       root  cwd   unknown                                /proc/391/cwd (readlink: Permission denied)
jbd2/sda5   391       root  rtd   unknown                                /proc/391/root (readlink: Permission denied)
jbd2/sda5   391       root  txt   unknown                                /proc/391/exe (readlink: Permission denied)
jbd2/sda5   391       root NOFD                                          /proc/391/fd (opendir: Permission denied)
ubuntu@ubuntu:~$ sudo lsof | grep sda5
 
lsof: WARNING: can't stat() vfat file system /casper-rw-backing
      Output information may be incomplete.
lsof: WARNING: can't stat() ext2 file system /cow
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs
      Output information may be incomplete.
jbd2/sda5   391       root  cwd       DIR       0,16      4096          2 /
jbd2/sda5   391       root  rtd       DIR       0,16      4096          2 /
jbd2/sda5   391       root  txt   unknown                                 /proc/391/exe
ubuntu@ubuntu:~$ 

```
 
thanks
-Jaob99

---

### Post by Rubi1200 on 2011-04-25
Okay, well it looks as if the process 391 is holding your partition.

Try this from the LiveCD:

```
sudo kill 391
```

After running this, and assuming it doesn't throw any errors, try and run the boot script we mentioned before.

You may also still need to turn swap off.

---

### Post by jaob99 on 2011-04-25
hello Rubi1200.
i ran ```
sudo kill 391
```but it said "no such process"
```
 
ubuntu@ubuntu:~$ sudo swapoff -a
ubuntu@ubuntu:~$ sudo kill 391
kill: No such process

```
so i ran the lsof command again...
```

ubuntu@ubuntu:~$ sudo lsof | grep sda5
lsof: WARNING: can't stat() vfat file system /casper-rw-backing
      Output information may be incomplete.
lsof: WARNING: can't stat() ext2 file system /cow
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs
      Output information may be incomplete.
jbd2/sda5   410       root  cwd       DIR       0,16      4096          2 /
jbd2/sda5   410       root  rtd       DIR       0,16      4096          2 /
jbd2/sda5   410       root  txt   unknown                                 /proc/410/exe
ubuntu@ubuntu:~$ sudo kill 410

```
so i killed that "410" process, there were no errors :).
and ran the boot info script...
```

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 

```
and it got stuck again :(.
 
thank you for helping
-Jaob99

---

### Post by coffeecat on 2011-04-25
> **jaob99 said:**
> 
```

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 

```and it got stuck again :sad:.

Ok, the problem with sda5 is consistent. Go back to Rubi1200's post at post #20. 

Do...

```
lsof | grep sda5
```... again to get the PID, and then...

```
sudo kill <PID>
```... to kill that process. But now instead of trying to run the bootscript, try Rubi1200's suggestion to attempt to repair sda5 from the terminal with...

> **Rubi1200 said:**
> 
```
sudo e2fsck -f -y -v /dev/sda5
```

You might want to try running...

```
sudo swapoff -a
```... before running the e2fsck command. It may not be necessary but it shoudn't do any harm.

---

### Post by jaob99 on 2011-04-25
hi,
i ran the commands and this is the output i got:
```
 
ubuntu@ubuntu:~$ sudo lsof | grep sda5
lsof: WARNING: can't stat() vfat file system /casper-rw-backing
      Output information may be incomplete.
lsof: WARNING: can't stat() ext2 file system /cow
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs
      Output information may be incomplete.
jbd2/sda5   386       root  cwd       DIR       0,16      4096          2 /
jbd2/sda5   386       root  rtd       DIR       0,16      4096          2 /
jbd2/sda5   386       root  txt   unknown                                 /proc/386/exe
ubuntu@ubuntu:~$ sudo kill 386
ubuntu@ubuntu:~$ sudo swapoff -a
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda5
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 

```
 
thank you for helping
Jaob99

---

### Post by coffeecat on 2011-04-26
Odd. You've killed the process involved with sda5, but still you get "e2fsck: Device or resource busy while trying to open /dev/sda5 Filesystem mounted or opened exclusively by another program?"

Two suggestions. Run "sudo lsof | grep sda5" and then kill the process that shows up. Now run "sudo lsof | grep sda5" again and see if a different process has popped up. Kill that. Now "sudo lsof | grep sda5" yet again and kill any new process, and keep on doing that until you don't get any processes showing up. Now, and only now, try running "sudo e2fsck -f -y -v /dev/sda5"

Second suggestion: We got so distracted by the boot script failing to run, that we never saw the output of fdisk. It may not help, but it would be useful to see what the partition table is like. From a live CD:

```
sudo fdisk -lu
```And post the output.

**EDIT**: and yet another thought. Earlier in the thread, Rubi1200 suggested the Slax CD, but it wouldn't boot for you. Did you check the md5sum of the downloaded Slax ISO? The md5sum is on the Slax website. It's possible the ISO was corrupted, so it might be worth re-downloading if there is any doubt. The only reason I suggest revisiting Slax is that you might avoid whatever process is blocking sda5 with a simpler distro.

**EDIT2**: Or Knoppix might be another live CD you might want to try. It's heavier than Slax but used to be very popular as a maintenance and repair CD. Home page here:

[http://www.knoppix.com/](http://www.knoppix.com/)

---

### Post by Rubi1200 on 2011-04-26
It is worth trying coffeecat's suggestions and I also have some:

Have a go at booting the LiveCD again, but when it starts up and you see the little stick man and Ubuntu logo, hit F6 and then Esc to see the boot line which will look something like this:
>  **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**Now, after quiet splash add noswap so it looks like this:
>  **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash noswap--**Then, Enter to continue the boot process.

Once at the live desktop, go to the terminal and run the following commands and post the output for us please:

```
cat /proc/mounts

cat /etc/fstab

sudo fdisk -l
```At the same time, if you booted with the noswap option, try the fsck command again and see if it still reports the drive as being busy.

---

### Post by jaob99 on 2011-04-26
hello coffeecat and Rubi1200
the output from sudo fdisk -lu.
 
```
ubuntu@ubuntu:~$ sudo fdisk -lu
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdc3a7039
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   229254476   114627207    7  HPFS/NTFS
/dev/sda2       229255166   312580095    41662465    5  Extended
/dev/sda5       229255168   309071871    39908352   83  Linux
/dev/sda6       309073920   312580095     1753088   82  Linux swap / Solaris
Disk /dev/sdb: 4041 MB, 4041211904 bytes
102 heads, 37 sectors/track, 2091 cylinders, total 7892992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8192     7892991     3942400    b  W95 FAT32
ubuntu@ubuntu:~$ 

```
 
and the output from the ```
 
cat /proc/mounts
cat /etc/fstab
sudo fdisk -l

``````
ubuntu@ubuntu:~$ sudo cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=958520k,nr_inodes=215691,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/sdb1 /cdrom vfat rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
/dev/sdb1 /casper-rw-backing vfat rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
/dev/loop1 /cow ext2 rw,noatime,errors=continue 0 0
aufs / aufs rw,noatime,si=dbef1653 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=999,group_id=999 0 0
/dev/sr0 /media/Ubuntu\04010.10\040i386 iso9660 ro,nosuid,nodev,relatime,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500 0 0
ubuntu@ubuntu:~$ sudo cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdc3a7039
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14271   114627207    7  HPFS/NTFS
/dev/sda2           14271       19458    41662465    5  Extended
/dev/sda5           14271       19239    39908352   83  Linux
/dev/sda6           19239       19458     1753088   82  Linux swap / Solaris
Disk /dev/sdb: 4041 MB, 4041211904 bytes
102 heads, 37 sectors/track, 2091 cylinders
Units = cylinders of 3774 * 512 = 1932288 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           3        2092     3942400    b  W95 FAT32
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda5
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 

```
 
thanks
-Jaob99 :)

---

### Post by Rubi1200 on 2011-04-27
Hi and thanks for the results. Should have thought of this before, but can you also post the output from this:

```
sudo blkid
```

Thanks.

---

### Post by coffeecat on 2011-04-27
@jaob99, there is something slightly odd about the fdisk output, but I'm not sure exactly what it means. You did both fdisk -lu and fdisk -l. The former reports in sectors, the latter in cylinders. The sectors output is more precise if one is looking for overlapping partitions or other illegalities, but in your case fdisk -l is showing something not right - or so it seems.

For sda, your fdisk -lu:

```
ubuntu@ubuntu:~$ sudo fdisk -lu
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdc3a7039
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   229254476   114627207    7  HPFS/NTFS
/dev/sda2       229255166   312580095    41662465    5  Extended
/dev/sda5       229255168   309071871    39908352   83  Linux
/dev/sda6       309073920   312580095     1753088   82  Linux swap / Solaris
```

Both sda2 and sda6 end on sector 312580095 which is comfortably before the end sector. I can't see anything wrong.

Your fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdc3a7039
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14271   114627207    7  HPFS/NTFS
/dev/sda2           14271       19458    41662465    5  Extended
/dev/sda5           14271       19239    39908352   83  Linux
/dev/sda6           19239       19458     1753088   82  Linux swap / Solaris
```

With this output sda2 and sda6 are reported as ending on cylinder 19458 whereas the disk is reported as having only 19457 cylinders. Since there's a cylinder 0, if a partition ends on 19458, that would make 19459 cylinders. Unless I'm missing something. 

I'll have a think about this but, in the meantime, did you try the repeated "sudo lsof | grep sda5" and "sudo kill <PID>" until there were no more processes to kill, or adding no swap to the boot options as Rubi1200 suggested?

---

### Post by Rubi1200 on 2011-04-27
After some consultation, coffeecat and I have asked another forum member, who is very knowledgeable in this area, to take a look and offer his perspectives.

Please wait for him or one of us to post something before you proceed with anything.

Thanks.

---

### Post by srs5694 on 2011-04-27
Rubi1200 asked me to take a look at this thread. My observations:


[list]
[*]It's puzzling, and perhaps troubling, that Slax failed to boot. I recommend trying [System Rescue CD](http://www.sysresccd.org/) and/or [PartedMagic.](http://partedmagic.com/) If you have problems booting more than one of these three discs, I'd strongly suspect a hardware problem.
[*]There was a case like this some months ago, in which somebody couldn't perform an fsck on a filesystem because it was in use. IIRC, the trouble was that some process was looking at the disk and getting locked in a loop trying to deal with the journal file. I only dimly recall that thread, though, and I specifically don't recall the resolution. You could try looking for that thread, but good luck finding it!
[*]The fact that fdisk shows the last partition ending at one over the disk's final cylinder is *not* a problem. I've seen that before, and I suspect it's because of the fact that most disks have a given number of "cylinders" (a fiction these days) plus some extra sectors. Those extra sectors are usable, so if the last partition ends in that area, the end "cylinder" will be one more than the maximum.
[*]I recommend running a SMART utility, such as GSmartControl, on the disk. SMART is a system for detecting disk hardware failures. I don't recall if GSmartControl is installed in the Ubuntu live CD or not, but if it's not installed you should be able to install it by opening a terminal and typing "sudo apt-get install gsmartcontrol". Once in the utility, double-click your disk and check the Attributes tab for anything untoward (problems are usually highlighted in red, IIRC). Also go to the Perform Tests tab and run at least a short self-test. If GSmartControl reveals problems, buy a replacement disk and back up the current one *immediately*.
[*]You could try doing a low-level copy of the problem partition to another device, or better yet to a file, and then check it there. This might work around some problems, particularly if you've got a failing disk or if you copy to a file so that the OS won't try to touch the filesystem until you tell it to. Of course, you'll need a disk with enough free space to do this. (If you don't, consider buying one and using it for backups after this crisis is over.) You can use dd to do a low-level copy, as in "dd if=/dev/sda5 of=/media/backup/sda5.img". This creates a copy of /dev/sda5 in the sda5.img file on the disk mounted at /media/backup. You can then run fsck on this file, as in "fsck /media/backup/sda5.img", and then copy it back to the original partition by reversing the if= and of= options in the original dd command.
[/list]

---

### Post by jaob99 on 2011-04-28
> **srs5694 said:**
> You could try doing a low-level copy of the problem partition to another device, or better yet to a file, and then check it there. This might work around some problems, particularly if you've got a failing disk or if you copy to a file so that the OS won't try to touch the filesystem until you tell it to. Of course, you'll need a disk with enough free space to do this. (If you don't, consider buying one and using it for backups after this crisis is over.) You can use dd to do a low-level copy, as in "dd if=/dev/sda5 of=/media/backup/sda5.img". This creates a copy of /dev/sda5 in the sda5.img file on the disk mounted at /media/backup. You can then run fsck on this file, as in "fsck /media/backup/sda5.img", and then copy it back to the original partition by reversing the if= and of= options in the original dd command.

hi srs5694,
 
this is the output fron the commands,
```
 
ubuntu@ubuntu:~$ sudo mkdir /media/backup
ubuntu@ubuntu:~$ sudo dd if=/dev/sda5 of=/media/backup/sda5.img
662888+0 records in
662888+0 records out
339398656 bytes (339 MB) copied, 37.6222 s, 9.0 MB/s
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /media/backup/sda5.img
e2fsck 1.41.12 (17-May-2010)
Error reading block 4751360 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes
Force rewrite? yes
Superblock has an invalid journal (inode 8).
Clear? yes
*** ext3 journal has been deleted - filesystem is now ext2 only ***
Superblock has_journal flag is clear, but a journal inode is present.
Clear? yes
The filesystem size (according to the superblock) is 9977088 blocks
The physical size of the device is 82861 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes
ubuntu@ubuntu:~$
 

```
 
thanks for helping,
-Jaob99

---

### Post by jaob99 on 2011-04-29
hi Rubi1200,
earlier in the thread you said to post the output from 
```
 
sudo blkid

```
> **Rubi1200 said:**
> Hi and thanks for the results. Should have thought of this before, but can you also post the output from this:
 
```
sudo blkid
```
 
Thanks.
 
here it is:
```
 
subuntu@ubuntu:~$ sudo swapoff -a
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="37d8f4e4-2c5d-c24b-88c1-f21cd27f32c1" TYPE="ext2" 
/dev/sda1: LABEL="Local Disk" UUID="180068140067F6E2" TYPE="ntfs" 
/dev/sda5: UUID="9da46bca-954a-4436-82c7-d336b44d24c2" TYPE="ext4" 
/dev/sda6: UUID="5d371087-d826-486b-bdb1-57e262e57788" TYPE="swap" 
/dev/sdb1: LABEL="MYLINUXLIVE" UUID="4AAB-7B87" TYPE="vfat" 
ubuntu@ubuntu:~$ 
 

```
 
Thanks,
Jaob99

---

### Post by JohnMac on 2011-04-29
Hi Jaob99

I have had this problem several times while using 10.10 and I might have had this problem using 10.04 as well. As usual I pulled my hair out for awhile, thinking of all the effort involved in getting my config just right again and with the family breathing down my neck. I hope you are to find a fix before you have to reinstall.
As you can see I don't have a dual boot so I don't think it is a wubi problem.

How I solved this problem was to boot up using my LiveCD go into Gparted, highlight my boot partition and select "Check"

- Didn't work! you say

Initially I got an error message as well, can't remember what is was, and I had to bang out.

What I had to do was try another LiveCD eg Although my install was 10.10 I used my old 10.04 cd and it worked! Wifey thought I was genius.

Can't explain why this happens, but I did notice that there was a little 1Mb partition in front of my boot partition that did not appear with the other Gparted.

Good luck:P


System: Desktop AMD 64X2 5200+ CPU
RAM : 2G
Drive: Samsung 160G 
Distro: Maverick 10.10
Linux 2.6.35-28 generic
Desktop: Gnome 2.32.0

---

