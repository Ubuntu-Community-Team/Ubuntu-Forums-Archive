---
title: "grub error 15"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-07-16
let  me know what you need from me and we will proceed iorderly manner.

okay here is an out put
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4079    32764536   83  Linux
/dev/sda2           38209       38913     5662912+   5  Extended
/dev/sda3            4080       34675   245762370   83  Linux
/dev/sda4           34676       38208    28378822+  83  Linux
/dev/sda5           38209       38913     5662881   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

note i get error 15 when i boot up in normal manner

note i tried to do this but either it didnt work or i did somethng wrong
[http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/](http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/)

note i cant find an accepatble option to put after hd 0, that works

tks

---

### Post by rburkartjo on 2010-07-16
note i am using live cd now only way can boot up.

---

### Post by rburkartjo on 2010-07-16
also this output

ubuntu@ubuntu:~$ ls /boot/grub/
ls: cannot access /boot/grub/: No such file or directory
ubuntu@ubuntu:~$

---

### Post by Rubi1200 on 2010-07-16
Since you are using the LiveCD and can get online, please click on the link at the bottom of my post and follow the instructions there.

Post the results back here and we will see what we can do to help.

---

### Post by rburkartjo on 2010-07-16
rubi here are the results
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 64610103 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    65,529,134    65,529,072  83 Linux
/dev/sda2         613,811,520   625,137,344    11,325,825   5 Extended
/dev/sda5         613,811,583   625,137,344    11,325,762  82 Linux swap / Solaris
/dev/sda3          65,529,135   557,053,874   491,524,740  83 Linux
/dev/sda4         557,053,875   613,811,519    56,757,645  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1d143b49-0906-442a-944e-eccbee35b58d   ext3                                     
/dev/sda3        c0d03beb-86a8-4841-b6c7-32df5e376663   ext2                                     
/dev/sda4        9028b62a-91b0-45c5-9dae-febc59008263   ext3                                     
/dev/sda5        4dce963f-5a4a-4d91-9196-09b1d6ef8c76   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext3       (rw)


=================== sda1: Location of files loaded by Grub: ===================


  33.0GB: boot/grub/stage2
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

tks

---

### Post by Rubi1200 on 2010-07-16
Hi,

a couple of questions:

1) what version of Ubuntu do you have installed (or other Linux distro)?

2) what do you have on > sdb sdc sdd sdeThere is definitely something not right here.

First, you have GRUB-legacy which is an older version of GRUB.

Secondly, something has got messed up here:

> Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 64610103 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.

GRUB error 15 usually means everything is okay with your drives and partitions. But, the files that GRUB needs to boot cannot be located (usually as a result of installing them to the wrong device etc.)

---

### Post by rburkartjo on 2010-07-16
rubi and running linux mint 9

how do i find what is on sdb,sdc,sdd,sde

for i can post the output
i was using sudo fsck to repair some minor errors on the live cd and the info i received on how to do from one of the members of my linux board was incorrect. stuff happens

---

### Post by rburkartjo on 2010-07-16
just for your info i ran sudo fsck /dev/sda1 -f-y amd that caused the problem.

---

### Post by Rubi1200 on 2010-07-16
Linux Mint is based on Ubuntu. Therefore, the most recent versions 9, and I believe 8 too, use GRUB2. But you have GRUB-legacy on the MBR.

Normally, I would suggest reinstalling GRUB to the MBR.

However, in the interests of not causing further problems, I suggest you wait until one of the more experienced forum members comes along with a solution.

Hang in there and thanks for providing the information thus far.

:)

---

### Post by rburkartjo on 2010-07-16
rubi tks for all your help will leave this thread opened then. my daughter hates it when i pouch my puter

---

### Post by rburkartjo on 2010-07-16
/dev/sda1 ext3 /mnt   this should be my mount point

---

### Post by Rubi1200 on 2010-07-16
> **rburkartjo said:**
> just for your info i ran sudo fsck /dev/sda1 -f-y amd that caused the problem.

I searched the man pages for fsck and I don't see an -f switch. 

Are you sure that is what you used?

---

### Post by Rubi1200 on 2010-07-16
I am not sure if you should attempt to reinstall GRUB at this point.

You would be better off waiting in my opinion.

---

### Post by NFblaze on 2010-07-16
I dont know how borked it is but try this [https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found]("https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found").

---

### Post by Rubi1200 on 2010-07-16
> **NFblaze said:**
> I dont know how borked it is but try this [https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found](https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found).

I understand you want to help but did you read what is written there?

 > **Please note that the Live CD must be the same as the system you are fixing - either 32-bit or 64-bit** (if not then the **chroot** will fail). 

The OP is using Linux Mint not Ubuntu and even though LM is based on Ubuntu there are differences.

I would be very wary in such a case.

---

### Post by rburkartjo on 2010-07-16
nf tks but didnt work

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4079    32764536   83  Linux
/dev/sda2           38209       38913     5662912+   5  Extended
/dev/sda3            4080       34675   245762370   83  Linux
/dev/sda4           34676       38208    28378822+  83  Linux
/dev/sda5           38209       38913     5662881   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
ubuntu@ubuntu:~$

---

### Post by rburkartjo on 2010-07-16
rubi was worth trying nf'sx idea. will wait as you advise for more advanced advise. know there is a way to fix. i just dont know it

---

### Post by NFblaze on 2010-07-16
**Rubi1200**
> **Rubi1200 said:**
> I understand you want to help but did you read what is written there?

 

The OP is using Linux Mint not Ubuntu and even though LM is based on Ubuntu there are differences.

I would be very wary in such a case.

What are you talking about? He has an issue with grub. The commands listed in that section of the wiki are related to grub. Grub is OS independent. I used that manual last week to fix a grub issue with Backtrack-WinVista-WinXP boot problem. Took forever but it was finally done.


**rburkartjo:**

Try this (you are using the LiveCD right?):

```
sudo su
umount /dev/sda1
mkdir /mnt/dev /mnt/proc /mnt/sys
mount /dev/sda1 /mnt

mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys

chroot /mnt

dpkg-reconfigure grub-pc
```

Though it might fail around the dpkg-reconfigure. I know my issue was much much worse. As I had a grub-legacy/grub2 conflict.

---

### Post by rburkartjo on 2010-07-16
nf

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# umount /dev/sda1
root@ubuntu:/home/ubuntu# mkdir /mnt/dev /mnt/proc /mnt/sys
root@ubuntu:/home/ubuntu# mount /dev/sda1 /mnt
root@ubuntu:/home/ubuntu# 
root@ubuntu:/home/ubuntu# mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
root@ubuntu:/home/ubuntu# mount --bind /proc /mnt/proc
mount: mount point /mnt/proc does not exist
root@ubuntu:/home/ubuntu# mount --bind /sys /mnt/sys
mount: mount point /mnt/sys does not exist
root@ubuntu:/home/ubuntu# 
root@ubuntu:/home/ubuntu# chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
root@ubuntu:/home/ubuntu# 
root@ubuntu:/home/ubuntu# dpkg-reconfigure grub-pc
Package `grub-pc' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: grub-pc is not installed
root@ubuntu:/home/ubuntu#

---

### Post by rburkartjo on 2010-07-16
nf got a rub> when i reboot

---

### Post by SoFl W on 2010-07-16
[**Grub Err 15**]("https://wiki.ubuntu.com/Grub2#Err15")

(This should be in reoccurring discussions)

---

### Post by NFblaze on 2010-07-16
Ok so you have the grub shell now. 

Although, apparently the bind for the files didnt create because the directories didnt create or something. I dont know if you should go from here or if you should go back and retry that AND MAKE SURE the directories create and bind properly (/mnt/dev /mnt/proc /mnt/sys.

I think that might be safest and might be make the least amount of work if it is successful this time. So load back the LiveCD...(also which LiveCD version are you using because you have Grub 1 and although you technically could install Grub2 with one of the newer LiveCDs it's a pain in the *** and not fun to do over the internet so make sure you are using the LiveCD with Grub1)

So load the CD and restart into the operating system.

Go back enter in these commands:

sudo su
umount /dev/sda1
mkdir -v /mnt/dev /mnt/proc /mnt/sys
mount -v /dev/sda1 /mnt

mount --verbose --bind /dev /mnt/dev
mount --verbose --bind /proc /mnt/proc
mount --verbose --bind /sys /mnt/sys

chroot /mnt

dpkg-reconfigure grub

Dont restart if you get errors, this time.

---

### Post by rburkartjo on 2010-07-16
nf here is what i got should i reboot

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# umount /dev/sda1
root@ubuntu:/home/ubuntu# mkdir -v /mnt/dev /mnt/proc /mnt/sys
mkdir: created directory `/mnt/dev'
mkdir: created directory `/mnt/proc'
mkdir: created directory `/mnt/sys'
root@ubuntu:/home/ubuntu# mount -v /dev/sda1 /mnt
mount: you didn't specify a filesystem type for /dev/sda1
       I will try type ext3
/dev/sda1 on /mnt type ext3 (rw)
root@ubuntu:/home/ubuntu# 
root@ubuntu:/home/ubuntu# mount --verbose --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
root@ubuntu:/home/ubuntu# mount --verbose --bind /proc /mnt/proc
mount: mount point /mnt/proc does not exist
root@ubuntu:/home/ubuntu# mount --verbose --bind /sys /mnt/sys
mount: mount point /mnt/sys does not exist
root@ubuntu:/home/ubuntu# 
root@ubuntu:/home/ubuntu# chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
root@ubuntu:/home/ubuntu# 
root@ubuntu:/home/ubuntu# dpkg-reconfigure grub

---

### Post by NFblaze on 2010-07-16
What does ```
ls -l /mnt/
``` spit out?

---

### Post by rburkartjo on 2010-07-16
nl here is the spit
ubuntu@ubuntu:~$ ls -l /mnt/
total 88
drwxr-xr-x   3 root root  4096 2010-07-16 19:38 boot
drwx------ 141 root root 81920 2010-07-16 16:48 lost+found
ubuntu@ubuntu:~$

---

### Post by lindsay7 on 2010-07-16
never mind, it was already tried.

---

### Post by rburkartjo on 2010-07-16
lin tks anyway

---

### Post by NFblaze on 2010-07-16
Kinda like I expected, you have a separate /boot/ partition. Jeez man you gotta tell us these things. I hope also you are using the correct LiveCD like I mentioned earlier. If not your probrably creating a large headache for yourself and Im prolly gonna go get some food later on.

OK so, try this now.
(I'm gonna guess and say sda3 is the main Linux partition if its not use sda4.)

ls -r /mnt/

mkdir /mnt2 /mnt2/sys /mnt2/proc /mnt2/dev
mount /dev/sda3 /mnt2/
mount --verbose --bind /dev /mnt2/dev
mount --verbose --bind /proc /mnt2/proc
mount --verbose --bind /sys /mnt2/sys
chroot /mnt2
grub-install --root-directory=/mnt/ /dev/sda --force

---

### Post by rburkartjo on 2010-07-16
nf

ubuntu@ubuntu:~$ ls -r /mnt/
lost+found  boot
ubuntu@ubuntu:~$ mkdir /mnt2 /mnt2/sys /mnt2/proc /mnt2/dev
mkdir: cannot create directory `/mnt2': Permission denied
mkdir: cannot create directory `/mnt2/sys': No such file or directory
mkdir: cannot create directory `/mnt2/proc': No such file or directory
mkdir: cannot create directory `/mnt2/dev': No such file or directory
ubuntu@ubuntu:~$ mount /dev/sda3 /mnt2/
mount: only root can do that
ubuntu@ubuntu:~$ mount --verbose --bind /dev /mnt2/dev
mount: only root can do that
ubuntu@ubuntu:~$ mount --verbose --bind /proc /mnt2/proc
mount: only root can do that
ubuntu@ubuntu:~$ mount --verbose --bind /sys /mnt2/sys
mount: only root can do that
ubuntu@ubuntu:~$ chroot /mnt2
chroot: cannot change root directory to /mnt2: No such file or directory
ubuntu@ubuntu:~$ grub-install --root-directory=/mnt/ /dev/sda --force
Unrecognized option `--force'
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.

---

### Post by rburkartjo on 2010-07-16
ubuntu@ubuntu:~$ ls -r /mnt/
lost+found  boot
ubuntu@ubuntu:~$ mkdir /mnt2 /mnt2/sys /mnt2/proc /mnt2/dev
mkdir: cannot create directory `/mnt2': Permission denied
mkdir: cannot create directory `/mnt2/sys': No such file or directory
mkdir: cannot create directory `/mnt2/proc': No such file or directory
mkdir: cannot create directory `/mnt2/dev': No such file or directory
ubuntu@ubuntu:~$ mount /dev/sda4 /mnt2/
mount: only root can do that
ubuntu@ubuntu:~$ mount --verbose --bind /dev /mnt2/dev
mount: only root can do that
ubuntu@ubuntu:~$ mount --verbose --bind /proc /mnt2/proc
mount: only root can do that
ubuntu@ubuntu:~$ mount --verbose --bind /sys /mnt2/sys
mount: only root can do that
ubuntu@ubuntu:~$ chroot /mnt2
chroot: cannot change root directory to /mnt2: No such file or directory
ubuntu@ubuntu:~$ grub-install --root-directory=/mnt/ /dev/sda --force
Unrecognized option `--force'
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.

---

### Post by NFblaze on 2010-07-16
Did you close the previous terminal? Now you have to start again from the top since you are no longer root. 

Anyway, Im about to go to bed soon, but if you cant get it this time. I will suggest chalking it up and reinstalling, cuz grub reinstallation can be more trouble than its worth.

---

### Post by rburkartjo on 2010-07-16
nf tks for all your help if i cant get it to work will reinstall

---

### Post by rburkartjo on 2010-07-16
ging to leave this thread open all night if anyone has any ideas let me know if not will do a clean install/tks

---

### Post by rburkartjo on 2010-07-17
think the problem was that i used a live ubuntu cd to repair linux mint

---

