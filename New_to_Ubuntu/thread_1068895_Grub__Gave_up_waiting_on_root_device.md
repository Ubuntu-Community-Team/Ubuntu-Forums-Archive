---
title: "Grub : Gave up waiting on root device"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by aas452 on 2009-02-13
I think this might be a grub issue and it not seeing the correct device. Here is my error screen :

Boot from (hd 0,0) ext 3 00ad768f-79cf-...... (the Hard Drive Number continues)

Starting up

Loading; Please Wait

Gave up waiting for root device

Alert 
/dev/disk/by-uuid 00ad768f-79cf-...... (the Hard Drive Number continues) 
does not exist. Droping to shell

in the shell I type in exit and the Ubuntu GUI loads.

Any thoughts on what the issue might be. My drive is a SCSI could the syntax for the hd be sda, I ran into something like that before.

Any thoughts???

---

### Post by drs305 on 2009-02-13
Please post the results of the following. We can check if grub's UUID listing matches the actual partition UUIDs and fstab (or you can look for yourself):
```

cat /boot/grub/menu.lst
sudo blkid -c /dev/null
cat /etc/fstab

```

---

### Post by aas452 on 2009-02-13
```


**@VOXEL:~$ cat /boot/grub/menu.lst**

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=00ad768f-79cf-48da-bc63-6fe5fab4a8a1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=00ad768f-79cf-48da-bc63-6fe5fab4a8a1

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		00ad768f-79cf-48da-bc63-6fe5fab4a8a1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=00ad768f-79cf-48da-bc63-6fe5fab4a8a1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		00ad768f-79cf-48da-bc63-6fe5fab4a8a1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=00ad768f-79cf-48da-bc63-6fe5fab4a8a1 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		00ad768f-79cf-48da-bc63-6fe5fab4a8a1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=00ad768f-79cf-48da-bc63-6fe5fab4a8a1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		00ad768f-79cf-48da-bc63-6fe5fab4a8a1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=00ad768f-79cf-48da-bc63-6fe5fab4a8a1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		00ad768f-79cf-48da-bc63-6fe5fab4a8a1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```


```

**@VOXEL:~$ sudo blkid -c /dev/null**

/dev/sda1: UUID="00ad768f-79cf-48da-bc63-6fe5fab4a8a1" TYPE="ext3" 
/dev/sda5: UUID="1eb8208b-0c6d-4887-8d22-43fc2cd72bf5" TYPE="swap" 

```



```

**@VOXEL:~$ cat /etc/fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=00ad768f-79cf-48da-bc63-6fe5fab4a8a1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1eb8208b-0c6d-4887-8d22-43fc2cd72bf5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdc1	/media/BACKUP 	ntfs	-3g force	0	0

```

Thanks for your help!!

---

### Post by avtolle on 2009-02-13
Does [http://www.ubuntu.com/getubuntu/releasenotes/810#Boot%20failures%20on%20systems%20with%20Intel%20D945%20motherboards](http://www.ubuntu.com/getubuntu/releasenotes/810#Boot%20failures%20on%20systems%20with%20Intel%20D945%20motherboards) help you at all?

---

### Post by drs305 on 2009-02-13
Your UUIDs all appear correct. Check avtolle's link to see if your motherboard might be the problem listed in the Release Notes. Even if it is not the brand listed you might try adding the "rootdelay=90" item to your boot options to see if that solves the problem. You could experiment with different values to see what works. If it doesn't, remove it to restore the original settings.

The first menu (**or whichever kernel you are going to boot**) added item would make the entry look like this:
```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		00ad768f-79cf-48da-bc63-6fe5fab4a8a1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=00ad768f-79cf-48da-bc63-6fe5fab4a8a1 ro quiet splash **rootdelay=90**  
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

```

---

### Post by aas452 on 2009-02-13
Cool, now do I add the command anywhere in menu.lst

or maybe my question is what is the kernal stanza

---

### Post by egalvan on 2009-02-13
> **aas452 said:**
> 
Any thoughts on what the issue might be.
** drive is a SCSI** 
could the syntax for the hd be sda, I ran into something like that before.

Any thoughts???

SCSI drives can take longer to spool up than most non-SCSI,
so using the **rootdelay=90 option** *drs05* gave may solve the problem.

GRUB is using *uuid* to identify the drive, so sda vice hda is a non-issue there.

(I use LABELS in my GRUB to ease drive changes, 
but that's another story)

ErnestG

---

### Post by aas452 on 2009-02-13
That did it!!

Adding the bootdelay=90 after the kernal seems to work with no problem. Thankyou

---

### Post by b1lancer on 2010-02-26
Hi all.

My Acer netbook has been running great for 3 months run. But now I'm having this same problem. If I try to boot normally I see the Ubuntu logo appear, stay for a while, and then nothing else. If I try using recovery mode, I get that gave up waiting message along with dropping to shell and a bunch of other stuff.

firstly, how do I add that root delay thing?

second, why did this happen? Can I change it back to it's original value after the change or do i just leave it?

One of the best things about Ubuntu was its fast boot up speed.

Thanks for your help.

---

### Post by b1lancer on 2010-02-27
I typed the commands from above:

```
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0AA4895EA4894D5F" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="B480923A80920352" LABEL="ACER" TYPE="ntfs" 
/dev/sda6: UUID="980807d9-f4e6-4097-8b08-c0778b9e1fde" TYPE="swap" 
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
```

---

### Post by b1lancer on 2010-02-27
I tried using a 9.10 live cd to access my files on the ubuntu partition that wont start up and I wasn't able to see them. It only shows the acer recovery and the windows one. Weird thing is the partition that holds the windows partition is listed as the full size of the hard drive.

Please someone help!! I have a multitude of files that were supremely important in Ubuntu beacsue  Ubuntu is supposed to be ultra reliable. In 2 years of using ubuntu I have never seen such a horrible failure like this.

---

### Post by drs305 on 2010-02-27
*blkid* didn't see the linux partition, only the swap partition. 

EDIT: Meierfra. pointed out that this is not a partition problem, so I am removing this post.

---

### Post by Miljet on 2010-02-27
> Weird thing is the partition that holds the windows partition is listed as the full size of the hard drive
This indicates to me that Ubuntu was installed with Wubi and the disk was never actually partitioned.

On second thought, there is apparently a swap partition so the drive had to be partitioned at some time.

---

### Post by b1lancer on 2010-02-27
No. I never used Wubi to install 9.10

Im doing the reading on test disk. I guess that's my only option, huh?

---

### Post by meierfra. on 2010-02-27
This does not sound like a partition table problem. 
**So do not use testdisk**
Hang on.

---

### Post by meierfra. on 2010-02-27
Please post the output of

```
sudo fdisk -lu
sudo blkid -p /dev/sda5
sudo hexdump  -s 0x410 -n 2 /dev/sda5
sudo mount -t ext4 /dev/sda5 /mnt
ls /mnt

```

(this assume that your ubuntu partition on /dev/sda5 and uses an ext4 file system)

---

### Post by b1lancer on 2010-02-27
Glad I didn't do anything! Thanks....

Just to confirm.... should I boot into the 9.10 live cd and type those commands?

---

### Post by meierfra. on 2010-02-27
Yes.

---

### Post by b1lancer on 2010-02-27
How do I know if it's sda5 or not?

(I'm loading into live cd now)

---

### Post by meierfra. on 2010-02-27
Just try it with /dev/sda5.  (no harm will be done if Ubuntu is not  on /dev/sda5)

---

### Post by b1lancer on 2010-02-27
ok. i tried different sda's just in case. Here are the results:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a0d38ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    14683409     7341673+  12  Compaq diagnostics
/dev/sda2   *    14684160   165851723    75583782    7  HPFS/NTFS
/dev/sda3       165855060   312576704    73360822+   5  Extended
/dev/sda5       165855123   306616589    70380733+  83  Linux
/dev/sda6       306616653   312576704     2980026   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo blkid -p /dev/sda5
/dev/sda5: ambivalent result (probably more filesystems on the device)
ubuntu@ubuntu:~$ sudo blkid -p /dev/sda1
/dev/sda1: UUID="0AA4895EA4894D5F" LABEL="PQSERVICE" TYPE="ntfs" USAGE="filesystem" 
ubuntu@ubuntu:~$ sudo blkid -p /dev/sda2
/dev/sda2: UUID="B480923A80920352" LABEL="ACER" TYPE="ntfs" USAGE="filesystem" 
ubuntu@ubuntu:~$ sudo blkid -p /dev/sda3
ubuntu@ubuntu:~$ sudo blkid -p /dev/sda4
ubuntu@ubuntu:~$ sudo hexdump  -s 0x410 -n 2 /dev/sda5
0000410 2468                                   
0000412
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda5 /mnt
ubuntu@ubuntu:~$ ls /mnt
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old

```

---

### Post by meierfra. on 2010-02-27
You have been hit by this bug:

[https://bugs.launchpad.net/ubuntu/+bug/518582](https://bugs.launchpad.net/ubuntu/+bug/518582)

Luckily  the fix is very easy: You just need to create a file on /dev/sda5
If you rebooted  the LiveCD since your last post do
```

sudo mount -t ext4 /dev/sda5 /mnt 

```
 In any case 
```
sudo touch /mnt/empty_file
```

Your problem  should be fixed.
Just to confirm wait a few seconds and then run

```
sudo blkid -p /dev/sda5

```
If you still get the   "ambivalent result" error message wait a little longer and run "sudo blkid -p /dev/sda5" again.

---

### Post by b1lancer on 2010-02-27
My Ubuntu had a bug!! :rolleyes:

Any way, I did what you suggested. Unfortunately I waited quite a while and I'm still getting an ambivalent result.

---

### Post by meierfra. on 2010-02-27
Hang on

---

### Post by meierfra. on 2010-02-27
Did you noticed  that I had added a missing sudo:

```
sudo touch /mnt/empty_file
```

If  you used "sudo" just reboot and see whether you can get into Ubuntu.
Otherwise  try  again with "sudo"

---

### Post by meierfra. on 2010-02-27
Just to make sure: post

```
 sudo hexdump  -s 0x410 -n 2 /dev/sda5
```

again.

---

### Post by b1lancer on 2010-02-27
```
ubuntu@ubuntu:~$  sudo hexdump  -s 0x410 -n 2 /dev/sda5
0000410 2467                                   
0000412

```

---

### Post by b1lancer on 2010-02-27
I did notice the sudo was missing because it told  me permission denied. I'm trying those again.

---

### Post by meierfra. on 2010-02-27
Looks good. Just reboot and see whether you can get into Ubuntu.

---

### Post by b1lancer on 2010-02-27
Here's what I got this time:

```
sudo mount -t ext4 /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo touch /mnt/empty_file
ubuntu@ubuntu:~$ sudo blkid -p /dev/sda5
/dev/sda5: UUID="821ba69f-67a2-4e83-93ea-058d4124ff5c" VERSION="1.0" TYPE="ext4" USAGE="filesystem" 
```

---

### Post by meierfra. on 2010-02-27
Looks even better.

---

### Post by b1lancer on 2010-02-27
[SIZE=4]**Yes!!!!**[/SIZE]  :D

You saved the day!! Thanks a billion!!

I owe you a be--- um... what's the official Ubuntu drink? Coffee?!

Thanks so much for your help my friend.

---

### Post by meierfra. on 2010-02-27
> My Ubuntu had a bug!!
Every singly Ubuntu 9.10 has this bug. Every time anybody   shuts down or reboots   Ubuntu 9.10, where is   1:16384 chance that Ubuntu will no longer  boot.
 

> Yes!!!!
Great.


> what's the official Ubuntu drink? Coffee?!

Probably. But I rather go for a  beer.


> Thanks so much for your help my friend. 
You are welcome.


If you have not done so yet, would you mind going  to the [bug report ]("https://bugs.launchpad.net/ubuntu/+bug/518582") and then click on 

"This bug affects x people" Does this bug affect you" ( or "This bug affects you)

to let launchpad know that you have been affected by the bug.
You might also leave a comment.   Thanks.

---

### Post by drs305 on 2010-02-28
meierfra.

Just read your bug report and solution. Don't know how you come up with this stuff, but - brilliant!

---

### Post by sundeepdude on 2010-03-16
Im also having a similar issue, I've tried rootdelay=90 and tried changing the UUID to /dev/sda5 but still nothing. The wired thing is it boots into ubuntu some times and otehr times i get the Gave up waiting on root device error.

---

### Post by b1lancer on 2010-03-24
Were you able to get it fixed? Booting from a live cd and running the commands from post #22 worked for me.

---

### Post by caldoverde on 2010-05-10
Hi, I have the same problem, but I get different outputs wich follow:

filipe@submachinegun:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: Ficheiro ou directoria inexistente (file or folder unexistent)



filipe@submachinegun:~$ sudo blkid -c /dev/null
[sudo] password for filipe: 
/dev/sda1: UUID="0af20e6e-7e4c-4207-b839-f0040a2b7a2b" TYPE="ext4" 
/dev/sda5: UUID="6926cc63-2b1e-4773-b4a8-9e065659ce10" TYPE="swap" 
filipe@submachinegun:~$ 



filipe@submachinegun:~$ cat /etc/fstab
filipe@submachinegun:~$                     (no output at all!!!)

Please helpm me!

---

### Post by caldoverde on 2010-05-15
Figured it out:

In 10.04, theres no menu.lst file, but grub.cfg does the job so I added rootdelay=90 in that file as mentioned earlier.

---

### Post by anonymouseGR on 2010-12-30
Issue still persisting in 10.10 with kernel 2.6.35-24 and all the latest updates

This post saved the day.
Thanks to all you guys.

p.s  adding  rootdelay=90 inside grub.cfg did it for me as well

---

### Post by 4md1t on 2010-12-31
[COLOR="DarkRed"][SIZE="5"]can someone tell me what the hell it means  ?[/SIZE][/COLOR]



[SIZE="4"]http://ge.tt/5hbXd17/RESULTS.txt
[/SIZE]
[SIZE="5"]
i have reinstalled Ubuntu Remix 4 times .. 
still have Booting Problem [/SIZE]

---

### Post by drs305 on 2010-12-31
4md1t,

Is your computer booting first to sdc? You may need to go into the BIOS setup and change the first boot device to your 250GB drive.

Another possibility is that your BIOS is only recognizing the first 137GB of your drive. Again in BIOS, you can check the disk size and make sure BIOS is seeing all the drive space (i.e. greater than 138GB). If it isn't, look for a setting to enable LBA or 'large disks' or something similar. Some of your G2 files are located well past the 137GB portion of your disk and the BIOS might not be capable of seeing the files during boot.

Also note that the Forum code of conduct discourages changing font sizes/colors unless it adds clarity to a post...  ;-)

---

### Post by Sorensiim on 2011-03-01
> **anonymouseGR said:**
> Issue still persisting in 10.10 with kernel 2.6.35-24 and all the latest updates

This post saved the day.
Thanks to all you guys.

p.s  adding  rootdelay=90 inside grub.cfg did it for me as well

Me too, GREAT JOB GUYS!

This was driving me insane!

---

