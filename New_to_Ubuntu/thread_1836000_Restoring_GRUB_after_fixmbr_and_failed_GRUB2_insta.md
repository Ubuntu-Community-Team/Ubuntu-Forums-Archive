---
title: "Restoring GRUB after fixmbr and failed GRUB2 install"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by Psycopatologic on 2011-08-30
Hi there,

Here at work is a desktop PC with Ubuntu and Xp dual boot. For some reason, XP crashed (maybe some sectors of the HDD are damaged) and kidnaped both NTFS partitions (the XP one and a 2TB HDD). I fixed the problem of the HDD with fixntfs, and everything was smooth. After that, i tryed to fix the XP boot problem and GRUB was wiped out in the process, only XP was able to boot with his blue screen. With a Ubuntu 11.04 32bits and following the How To tutorial ( [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) ) i tryed to restore GRUB, but i wasn't aware that the system had a different GRUB version. As far as i know the system was up to date, having Ubuntu 11.04 installed along with Windows XP (that's the Live CD that i was using), but it turns out that it has Ubuntu 8.04. After installing GRUB2 i followed the tutorial to purge GRUB2 by chroot with a 8.04 live cd and 11.04, but it tells me that it can't find the packages grub, grub-pc and grub-common. This is weird because when i reboot the machine the only thing that i see it's the GRUB 1.99 shell. Trying to find the grub.config file, the command find returns an error of uknown command, maybe the path is wrong as i read in the GRUB2 documentation. 

i've done the following

```
  grub> find /boot/grub/stage1 
```and it says "unknown command 'find'", but it has a sepparate boot partition so i done

```
find /grub/stage1
```gives me the same error.

when i do

```
 grub> ls 
```it returns

```
 (hd0) (hd0,msdos2) (hd0,msdos3) (hd0,msdos4) 
```i think GRUB can't read the partitions as sda.

I don't know what else to do, i would appreciate your help because there's some important data that i must be used the next days. I can't do a backup because we got some very important custom settings in some applications, and a backup don't solve the issue.

The system is 64 bits architecture, i don't know the hardware specifications because it's not my own pc, but it has Ubuntu 8.04 dual boot and XP pro. 

here's a list of the drives

First HDD:

sda1 - NTFS - Windows XP
sda2 - ext3 - Boot
sda3 - swap
sda4 - ext3 - /

sdb - NTFS - 2TB filesystem

I really appreciate your help.

---

### Post by seawolf167 on 2011-08-30
You might want to take a look at the [Super Grub Disk]("http://www.supergrubdisk.org/"), it should be able to solve all your issues.

---

### Post by Psycopatologic on 2011-08-30
> **seawolf167 said:**
> You might want to take a look at the [Super Grub Disk]("http://www.supergrubdisk.org/"), it should be able to solve all your issues.

Great!, i'll give that a try, i'll let you know, thanks!

---

### Post by Psycopatologic on 2011-08-30
After a couple of hours of reading and testing with Rescatux and Super Grub Disk, the problem still remains. Rescatux says that Grub cannot be installed because something went wrong, and Super Grub Disk don't boot from any partitions, actually it just stay on the main options screen.

---

### Post by Psycopatologic on 2011-08-30
[B]Update

[/B]I was able to reinstall GRUB from Ubuntu 8.04 Live CD, but i got some issues with the menu.lst file. Just after the instalation, every time that i turn on the pc it drives me to the GRUB shell.

Now, this is what i'm doing 

```
grub> find /boot/grub/stage1
(hd0,1)
(hd0,3)

```later

```
grub> root (hd0,1)
``````
grub> setup (hd0)
```it returns that staage1, stage2 and e2fs_stage1_5 exist, then it installs everything on hd0; but after reboot, it shows the grub shell again, i've done the same with hd0,1 ad hd0,3.

---

### Post by oldfred on 2011-08-30
If you have Ubuntu 11.04 you have grub2 not grub legacy. You are trying to install grub legacy with the repairs you are running. And with 11.04 you really need to have a liveCD that is 11.04 so you have grub2 1.99.


Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But if you have gotten grub legacy installed you may have to chroot into your system to uninstall both grub versions and cleanly reinstall grub2.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Psycopatologic on 2011-08-30
> **oldfred said:**
> If you have Ubuntu 11.04 you have grub2 not grub legacy. You are trying to install grub legacy with the repairs you are running. And with 11.04 you really need to have a liveCD that is 11.04 so you have grub2 1.99.


Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But if you have gotten grub legacy installed you may have to chroot into your system to uninstall both grub versions and cleanly reinstall grub2.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Actually Ubuntu 8.04 it's the current OS, i installed GRUB2 by mistake, by updating the WIndows MBR i managed to wipe out GRUB 1.99 from the system. Now i installed grub by a debian package that i found in the Ubuntu 8.04 package list by starting from the live cd and runing dpkg -i by running the system with chroot. Now, i'm able to run update-grub, i'll post the output of what i have done:

```
 root@ubuntu:/# grub-install /dev/sda
Searching for GRUB installation directory ... found: /boot/grub
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/sdb
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config*: No such file or directory
Updating /boot/grub/menu.lst ... done

root@ubuntu:/# grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,1)
 (hd0,3)
grub> root (hd0,1) 
root (hd0,1) 
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config*: No such file or directory
Updating /boot/grub/menu.lst ... done

root@ubuntu:/# reboot


``` 

Now, after the reboot i'm in the grub shell again

```
 [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub>
```

---

### Post by Psycopatologic on 2011-08-30
I finally did it!, i managed to reinstall grub from the scratch. By doing that i was driven to the starting point (grub shell), but now i let Rescatux configure everythig for me. It rebuild the menu.lst config and GRUB is back again. Thanks everyone for your time and your help, i really appreciate it.

---

### Post by Psycopatologic on 2011-08-31
I'll do a little explanation of how i solved my issue, may be still can help someone to fix the same issue in Ubuntu 8.04:

First: i uninstalled every grub package with this How to
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Second: i downloaded the same version of grub for my distro (Ubuntu 8.04) from the Ubuntu package source site 
[http://packages.ubuntu.com/hardy/grub](http://packages.ubuntu.com/hardy/grub)

Third: from the live cd go to the terminal (Applications>Accessories>Terminal) an then type

```
$cd /

$sudo -s -H

$mount -t ext3 /dev/**sda4** /mnt  #this is the main linux partition, you must replace with yours

$cp /path/ofthe/debian/package/grub_0.97-29ubuntu21_amd64.deb /mnt 

$mount -t proc proc /mnt/proc

$mount -t sysfs sys /mnt/sys

$mount -o bind /mnt/dev
```the best way to know the path of the file it's by drag and drop the file in the terminal window

Fourth: chroot, the name of the user must change from root@ubuntu to root@ubuntu#

```
$chroot /mnt /bin/bash 
```Fifth: installing grub

```
$dpkg -i grub_0.97-29ubuntu21_amd64.deb 
```it will work for a while and then, when it's ready, do a grub update to know everyting it's ok, it returns something like this.

```
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config*: No such file or directory
Updating /boot/grub/menu.lst ... done

```if everything goes well, follow the next step, if something goes wrong at this point do

```
$grub-install /dev/**sda** #you must replace sda for the name of your first bootable disk
```an the try to update grub again

Sixth: download Rescatux from here [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and burn it to a cd or make a booteable USB. Boot from it and do a grub restore following the instructions of the software. It'll say that everything goes ok. Now reboot and you will have your grub back.

Hope this can be useful for someone, because i think there's still some people using Ubuntu Hardy Heron like us, for more information of the grub restore process in hardy see the wiki [http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD)

---

