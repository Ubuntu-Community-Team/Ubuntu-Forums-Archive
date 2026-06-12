---
title: "GRUB fails upon install"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by d3mncln3r on 2010-01-28
I am a complete noob with linux but I wanted to give it a try. I have been trying to get Ubuntu to install, and it goes all the way to about 95% and then GRUB fails and it says system will not boot, or something to that effect. Here's a little background:
 
Trying to dual boot windows 7 and ubuntu, I created three partitions, one for windows, one for ubuntu, and one for storage. Windows also created a seperate partition for system restore.
 
Windows installed fine and operates perfectly on its 20G partition. When I try to install ubuntu on the other partition, I use ext3 and when that didnt work I used ext4. Still didn't work. The other thing is, I haven't specified a partition for swap space. Is that necessary? My processor is intel core 2 duo 2.4GHz and I have 3G of RAM. If I do need to create a seperate partition for swap space, how large should it be?
 
I've seen similar questions to mine in the forum, but nothing that addressed my issue, also when I have time I will try to post a boot info script (from this thread [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)) But right now I thought I would just try to get the problem out there. Feel free to ask for more info, and thanks in advance for any help!

---

### Post by d3mncln3r on 2010-01-29
Bump- at the risk of violating code of conduct... so is having a separate swap space partition completely necessary for install? I can't figure out why GRUB fails, any help?

---

### Post by cariboo on 2010-01-29
What version of Ubuntu are you trying to install, as it makes a difference if you are using grub-legacy or grub2.

---

### Post by d3mncln3r on 2010-01-29
I'm using ubuntu-9.10-desktop-i386.iso that i downloaded from the alternative downloads section at ubuntu.org I burned that to a DVD and ran the install from there.

---

### Post by kansasnoob on 2010-01-29
It really would be nice to see the output of the Boot Info script :)

---

### Post by d3mncln3r on 2010-01-29
Ok I will try to get that up in about an hour... thanks for the input!

---

### Post by d3mncln3r on 2010-01-29
Ok, I ran the boot info from the live CD, which I am currently running now, here are the results:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/mapper/isw_dghcgdcbcb_Volume0
isw_dghcgdcbcb_Volume01: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

isw_dghcgdcbcb_Volume02: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

isw_dghcgdcbcb_Volume03: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

isw_dghcgdcbcb_Volume04: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, 
                       isw_dghcgdcbcb_Volume04 starts at sector 0. But 
                       according to the info from fdisk, 
                       isw_dghcgdcbcb_Volume04 starts at sector 81915435.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: isw_dghcgdcbcb_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_dghcgdcbcb_Volume0: 240.1 GB, 240063348736 bytes
255 heads, 63 sectors/track, 29186 cylinders, total 468873728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4138620b

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_dghcgdcbcb_Volume01   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/isw_dghcgdcbcb_Volume02            206,848    40,962,047    40,755,200   7 HPFS/NTFS
/dev/mapper/isw_dghcgdcbcb_Volume03         40,965,750    81,915,434    40,949,685  83 Linux
/dev/mapper/isw_dghcgdcbcb_Volume04         81,915,435   468,873,089   386,957,655   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_dghcgdcbcb_Volume01 521AC5421AC523B7                       ntfs       System Reserved               
/dev/mapper/isw_dghcgdcbcb_Volume02 AA98E0D998E0A4D3                       ntfs                                     
/dev/mapper/isw_dghcgdcbcb_Volume03 9f397d66-fd8c-49bf-a3d8-d06ae5506496   ext4                                     
/dev/mapper/isw_dghcgdcbcb_Volume04 19794AB4737CD798                       ntfs       Storage                       
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_dghcgdcbcb_Volume0
isw_dghcgdcbcb_Volume01
isw_dghcgdcbcb_Volume02
isw_dghcgdcbcb_Volume03
isw_dghcgdcbcb_Volume04

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


====================== isw_dghcgdcbcb_Volume03/etc/fstab: ======================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/isw_dghcgdcbcb_Volume03 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

========== isw_dghcgdcbcb_Volume03: Location of files loaded by Grub: ==========


  20.9GB: boot/initrd.img-2.6.31-14-generic
  20.9GB: boot/vmlinuz-2.6.31-14-generic
  20.9GB: initrd.img
  20.9GB: vmlinuz
```

Hope that helps :)

---

### Post by meierfra. on 2010-01-29
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

Disclaimer: I have no personal experience with installing Grub on a fakeraid. I  don't know whether the instructions in  that thread are likely to succeed or  whether there are better methods to install Grub.

---

### Post by dolphinaura on 2010-01-29
[notrelavent]
aww man, you didnt resize using windows right?
if you didnt, and you cant boot up vista/7 after you fix grub, use the recovery disks. select repair.
[/notrelavent]

---

### Post by meierfra. on 2010-01-29
> windows is still somehow hogging the bootloader.

No.   The message

```
 Boot sector info:  According to the info in the boot sector, 
                       isw_dghcgdcbcb_Volume04 starts at sector 0. But 
                       according to the info from fdisk, 
                       isw_dghcgdcbcb_Volume04 starts at sector 81915435.
```
is  about the boot sector of the partition  the  "lsw_dghcgdcbcb_Volume04".  It's harmless, it would  only be  relevant if one would try to boot a Windows OS from that partition. But since there is not operating system on that partition it is irrelevant.

---

### Post by dolphinaura on 2010-01-29
> **meierfra. said:**
> No.   The message

```
 Boot sector info:  According to the info in the boot sector, 
                       isw_dghcgdcbcb_Volume04 starts at sector 0. But 
                       according to the info from fdisk, 
                       isw_dghcgdcbcb_Volume04 starts at sector 81915435.
```

is not about the partition table, but about the boot sector of the partition  the  "lsw_dghcgdcbcb_Volume04".  It's harmless, it would be only be  relevant if one would try to boot a Windows OS from that partition.

edit: misread. post fixed. didnt see that it said "boot sector info" at the front...

---

### Post by d3mncln3r on 2010-01-29
Ok thanks for the pointer... I am trying to follow those directions but having trouble at step 4: > 4. Mount the installation
**sudo mount /dev/mapper/nvidia_cffbdeda1 /mnt/root**
*If this fails use *nautilus* (*thunar* in xbuntu) to mount your Ubuntu root partition then use **mount** to find the mount location. This location will be used in place of **/mnt/root** in the following

first of all I'm not exactly sure which partition to use, when I use the "ls /dev/mapper" command there are quite a few more than I thought I had, look" ```
control                  isw_dghcgdcbcb_Volume03   isw_dghcgdcbcb_Volume0p3
isw_dghcgdcbcb_Volume0   isw_dghcgdcbcb_Volume04   isw_dghcgdcbcb_Volume0p4
isw_dghcgdcbcb_Volume01  isw_dghcgdcbcb_Volume0p1
isw_dghcgdcbcb_Volume02  isw_dghcgdcbcb_Volume0p2

```

According to GParted the partition I'm trying to use is Volume03, but then there is the option Volume0p3. Either way, I've tried substituting both of these and still, not working. Here are the results: ```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_dghcgdcbcb_Volume0p3
mount: can't find /dev/mapper/isw_dghcgdcbcb_Volume0p3 in /etc/fstab or /etc/mtab

```

I'm not frustrated, just looking forward to learning more about Ubuntu and linux in general. I know its going to be difficult so many thanks to those who stick with me and help me through this.

---

### Post by meierfra. on 2010-01-29
> I'm trying to use is Volume03, but then there is the option Volume0p3.
Sorry, don't know which one to use. You might try "sudo blkid" and see which partitions are listed. 

> ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_dghcgdcbcb_Volume0p3
mount: can't find /dev/mapper/isw_dghcgdcbcb_Volume0p3 in /etc/fstab or /etc/mtab

You are missing the mount point:

```
sudo mount /dev/mapper/isw_dghcgdcbcb_Volume0p3 [COLOR="Red"]/mnt/root[/COLOR]
```

---

### Post by d3mncln3r on 2010-01-29
Ok, update... I managed to get further down the steps, but it got a little rocky during the part where I have to uninstall grub, and then reinstall it, or something of the like, here are the steps I followed. Step 8 is where it stopped working for me > 4. Mount the installation
**sudo mount /dev/mapper/nvidia_cffbdeda1 /mnt/root**
*If this fails use *nautilus* (*thunar* in xbuntu) to mount your Ubuntu root partition then use **mount** to find the mount location. This location will be used in place of **/mnt/root** in the following steps.
**sudo mount --bind /dev /mnt/root/dev**
**sudo mount -t proc proc /mnt/root/proc**
**sudo mount -t sysfs sys /mnt/root/sys**[B][COLOR=#000000]
[/COLOR][/B]**sudo mount -t devpts devpts /mnt/root/dev/pts**[B]
sudo cp /etc/resolv.conf /mnt/root/etc/resolv.conf[/B]

5. Login into the installation
**sudo chroot /mnt/root /bin/bash**

6.Fetch most recent package lists[B]
apt-get update[/B]

7. Remove GRUB2
**apt-get purge grub2 grub-pc**
**rm -r /boot/grub**
##The system will be unbootable until another bootloader is installed.

      8. Install GRUB 0.97
**apt-get install grub**
**grub-install /dev/mapper/xxx** ##note please substitute your hdd in this line (mine would have been *nvidia_cffbdeda*) And here are my terminal results as I went along (they're quite long) ```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_dghcgdcbcb_Volume0p3 /mnt/root
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo mount -t proc proc /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -t sysfs sys /mnt/root/sys
ubuntu@ubuntu:~$ sudo mount -t devpts devpts /mnt/root/dev/pts
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/root/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
root@ubuntu:/# apt-get update
Err http://us.archive.ubuntu.com karmic Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com karmic-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done         
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/# milamber
milamber: command not found
root@ubuntu:/# apt-get update
Err http://us.archive.ubuntu.com karmic Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com karmic-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/# apt-get purge grub2 grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub2 is not installed, so not removed
Package grub-pc is not installed, so not removed
The following packages were automatically installed and are no longer required:
  grub-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 2,449kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 118659 files and directories currently installed.)
Removing grub-common ...
Processing triggers for sreadahead ...
Processing triggers for install-info ...
Processing triggers for man-db ...
root@ubuntu:/# rm -r /boot/grub
root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grub has no installation candidate
root@ubuntu:/# grub-install /dev/mapper/isw_dghcgdcbcb_Volume0p3
The program 'grub-install' can be found in the following packages:
 * grub
 * grub-pc
 * grub-coreboot
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-ieee1275
Try: apt-get install <selected package>
grub-install: command not found
root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grub has no installation candidate
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  grub-common
E: Package grub-pc has no installation candidate
root@ubuntu:/# apt-get install grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grub-common has no installation candidate
root@ubuntu:/# apt-get install grub-coreboot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-coreboot is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  grub-common
E: Package grub-coreboot has no installation candidate
root@ubuntu:/# apt-get install grub-ieee1275
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-ieee1275 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  grub-common
E: Package grub-ieee1275 has no installation candidate
root@ubuntu:/# 

```

Unfortunately, I probably won't have much internet access till tomorrow... thanks for the help, I will be back in the morning.

---

### Post by meierfra. on 2010-01-29
> Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
  Could not resolve 'us.archive.ubuntu.com'


It seems the internet connection is not working in the chroot.
I'm not sure what to do about this, but I'll do some research.
Without internet connection you won't be able to install grub. So this needs to be resolved before you can do anything else.  If you look at the thread, other people had the same problem.



> grub-install /dev/mapper/isw_dghcgdcbcb_Volume0p3
This needs to be 

```
grub-install /dev/mapper/isw_dghcgdcbcb_Volume0
```
(grub needs to be installed to the MBR of the hard drive, not the partition)

---

### Post by d3mncln3r on 2010-01-29
[QUOTE
(grub needs to be installed to the MBR of the hard drive, not the partition)[/QUOTE]

Ok, will this affect my windows 7 install? I'm not sure if there's enough space there.

---

### Post by meierfra. on 2010-01-29
> Ok, will this affect my windows 7 install? I'm not sure if there's enough space there.
The MBR is before any of the partition and so it does  not directly effect your Windows install.  If everything goes well, you will be able to boot into Windows 7 from the Grub menu. If things go wrong and we can't get Grub to work, you will have to restore the MBR, which is fairly easy to do. If  you want to be extra careful, I can show you how to backup your current MBR.

---

### Post by meierfra. on 2010-01-30
Let's try to  install grub without the "chroot" to avoid the internet connection problem
 
**Step 1 Setup some short cuts**
```
sudo -i     #get a root terminal
disk=/dev/mapper/$(dmraid -s -c)
part=$disk"3" 
echo $disk  # just for  checking, should  return /dev/mapper/isw_dghcgdcbcb_Volume0 

```


**Step 2 Backup your current MBR**

```
sudo dd if=$disk of=~/Desktop/mbr.bin count=63
```
Be very careful with the "dd" command. If it runs for more than a couple of second, kill the process with "Ctrl+c".
Save the file "mbr.bin"  (which should be on your Desktop) to some place outside your hard drive (flash drive, online storage)

**Step 3 Remove Grub 2 and install Grub**

```
apt-get purge grub-pc #Choose "yes" when asked to remove all  Grub 2 files, 
apt-get install grub
```


**Step 4 Copy the stage files to your Ubuntu partition**
```
mount $part /mnt
mkdir /mnt/boot/grub/  #Edit: left out this step
cp /usr/lib/grub/i386-pc/* /mnt/boot/grub  #Edit: needs to be "x86_64-pc" for 64bit,  
```


**Step 5 Install grub to the MBR**

```
echo "(hd0) $part" >/mnt/boot/grub/device.map
grub --no-curses --device-map=/mnt/boot/grub/device.map
```
and at the grub prompt:


```

find /boot/grub/stage2 #just for checking, should return (hd0,2)
root (hd0,2)
setup (hd0)
quit

```


**Step 6 Create menu.lst**

```
gedit /mnt/boot/grub/menu.lst
```
This will open a blank file.

Type the following into the file:

```
default 0
timeout 10

title  Ubuntu
root (hd0,2)
kernel /vmlinuz root=/dev/mapper/isw_dghcgdcbcb_Volume03 ro
initrd /initrd.img

title Windows 7
root (hd0,0)
chainloader +1

```
Save the file.

Reboot and see whether the grub menu appears. Try to boot into both 0S's
Report any error messages.

You might also try the whole  thing  replacing all "3"'s by "p3".


Once you booted into Ubuntu, you will have to do some more work, so that your MBR does  not get overwritten by Grub2 during updates. We'll worry about that later. For now just decline any updates.

---

### Post by d3mncln3r on 2010-01-30
great... i'll try this when i get home... no internet connection there, but I wont need right?

---

### Post by meierfra. on 2010-01-30
You still need an internet connection to install grub.

---

### Post by meierfra. on 2010-01-30
To avoid the internet connection: Download the  deb file for grub from [here]("http://packages.ubuntu.com/karmic/i386/grub/download")
Take it home on a flash drive. Follow the instruction, but  skip "apt-get install grub". At that point  double click the deb file  and then click on "install.

---

### Post by d3mncln3r on 2010-01-31
Ok, so I wasn't able to try this last night (forgot flash drive) but I just tried it right now, and I am connected to the internet so I followed your steps exactly. Everything worked out until, step number 4 > 
**Step 4 Copy the stage files to your Ubuntu partition** When I tried the code, I recieved this error ```
cp: cannot stat `/usr/lib/grub/i386-pc/*': No such file or directory
``` I looked through my "places" and followed usr>lib>grub and found there was no i386-pc directory, I found a directory called x86_64-linux-gnu. idk why but I thought that might help. But I won't do anything till I hear back from you regardless. Thanks!

---

### Post by meierfra. on 2010-01-31
Do you have  64 bit computer?  Anyway, the folder should contain files like

```
e2fs_stage1_5  jfs_stage1_5    reiserfs_stage1_5  stage2           xfs_stage1_5
fat_stage1_5   minix_stage1_5  stage1             stage2_eltorito

```

If it does, just use  that folder in place of "i386-pc"

---

### Post by d3mncln3r on 2010-01-31
yeah I have 64 bit win 7 running, I will check for those files, what is the 'file search' option with ubuntu? (like I said brand spaking new with this :))

---

### Post by meierfra. on 2010-01-31
They aren't in "/usr/lib/grub/x86_64-linux-gnu.idk  ?

---

### Post by d3mncln3r on 2010-01-31
ok, the directory that contained those files was x86_64-pc, when I initiated command ```
cp /usr/lib/grub/x86_64-pc/* /mnt/boot/grub
```I get the error, ```
cp: target  '/mnt/boot/grub' is not a directory
```

when I go to /mnt/boot there are 7 files but none of them is a folder called 'grub'

---

### Post by meierfra. on 2010-01-31
My bad. Just create the direcory


```
mkdir /mnt/boot/grub
```

---

### Post by d3mncln3r on 2010-01-31
ok when I get to the grub prompt and execute the first command, I get the following error
```
grub> find /boot/grub/stage2
find /boot/grub/stage2

Error 15: File not found

```

---

### Post by meierfra. on 2010-01-31
> grub> find /boot/grub/stage2
find /boot/grub/stage2

Error 15: File not found
Just to double check:  See whether you have "stage2" in /mnt/boot/grub.

Also try (at the grub prompt):

```
device (hd0) /dev/mapper/isw_dghcgdcbcb_Volume0
find /boot/grub/stage2
```

If it returns (hd0,2), continue with the instructions. If not, come back here.

---

### Post by d3mncln3r on 2010-01-31
Ok when I execute the find command, it comes back file not found, but when I use the file explorer to /mnt/boot/grub I do see stage2 in there

---

### Post by meierfra. on 2010-01-31
Well, its seems Grub cannot read your raid partition. And I have no idea how to fix that.  Does "ls /dev/mapper" still return "isw_dghcgdcbcb_Volume0p3" and "isw_dghcgdcbcb_Volume03"?

 If yes, you might try again: 

For step1 just do

 ```
part=$disk"p3"  
```

You  won't have to do "Step 2" and "Step 3" again..

---

### Post by d3mncln3r on 2010-01-31
ok ls /dev/mapper only returns ```
control isw_dghcgdcbcb_Volume0
 isw_dghcgdcbcb_Volume01
 isw_dghcgdcbcb_Volume02
 isw_dghcgdcbcb_Volume03
 isw_dghcgdcbcb_Volume04
```
 
I'm thinking this might be a good thing?

---

### Post by meierfra. on 2010-01-31
> I'm thinking this might be a good thing?
Yes. That's good. But it also means that I'm out of ideas what do to next (Sorry, I'm not an expert in raid) You might have a look at post 40 in the thread a linked earlier: [http://ubuntuforums.org/showthread.php?t=1360445#40](http://ubuntuforums.org/showthread.php?t=1360445#40)
(but if you still don't get an internet connection in  the chroot, it won't work)

---

### Post by d3mncln3r on 2010-01-31
Ok well I want to thank you with all the help you've given me so far, in any case I'm starting to learn about linux and that is the goal. I tried just one more thing, it didn't work properly, but maybe if I start over with your steps that we've talked about, it might. With GParted I deleted the partition that I had used to install ubuntu, then I ran the ubunut installation all over again, I set up a new partition space and set the mount point to "/" then ran the installer. At the end, as it had before, I got the error that grub had not installed properly. But now I will try to go through all the points that you had given me before. If it continues to not work, then I guess I have some more searching to do. Thanks again!

---

### Post by meierfra. on 2010-02-14
You might have already see this  link in the FakeRaid Howto thread:

[http://neosmart.net/forums/showthread.php?t=5761](http://neosmart.net/forums/showthread.php?t=5761)

Somebody was able to overcome his fake raid problems by using EasyBCD and NeoGrub.  That might be worth a try.

---

