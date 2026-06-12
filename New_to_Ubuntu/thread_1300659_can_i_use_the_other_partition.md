---
title: "can i use the other partition??"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by ni ni on 2009-10-25
hello all

in "Places" i have Computer, DVD drive and 30.1GB Media.

When i dropped my laptop, i apparently damaged the HDD. I partitioned the drive, put Linux on one partition, and this 30.1 GB media is the second part of the original (only 80 gb!)

Question is: can i do anything with this 30GB partition? i could do with some space!  The laptop is old and kind of hanging on by one leg, but i have no money for a new one for at least 2 years, so trying to make do with what i have (god bless linux!)

It may have bad sectors, i don't even know how to test it.  if i try to save anything to the media it says Permission Denied.

I know i'm gonna have to give ye more information, but i don't know what presently.  hope ye can help xx

thanks in advance for any tips x x x x:KS:KS:KS:KS

---

### Post by prshah on 2009-10-25
> **ni ni said:**
> 
Question is: can i do anything with this 30GB partition? 

It may have bad sectors, i don't even know how to test it.  

Do you have a partition / file system on that partition, or is it unpartitioned (blank space)? If you already have a partition is it NTFS or ext3 (linux)? If it is blank, please create a partition on it using gparted.

If you want the partition to be automatically (statically) mounted, you need to add the specific information to the /etc/fstab file. For example, you need to add an entry such as ```
# /dev/sda6
[color=red]UUID=AB707BCE707F8DE8[/color] [color=blue]/media/sda6[/color]     ext3    [color=green]defaults,relatime,auto[/color] 0       1
``` For an NTFS /FAT32 partition the entry will change to ```
# /dev/sda6
[color=red]UUID=AB707BCE707F8DE8[/color] [color=blue]/media/sda6[/color]     ntfs    [color=green]defaults,umask=007,gid=46[/color] 0       1
```

In the above example (your details will differ), you can find out the correct UUID for your partition (the part in red) using the command```
sudo blkid /dev/sda6
``` (Replace sda6 with the actual partition device ID in your case).

You should also create the mount point (the part in blue)```
sudo mkdir /media/sda6
sudo chown root:plugdev /media/sda6

```

Note that if the filesystem on that partition is ext3, directories / files subsequently created on the mounted drive will carry ownership / permissions relevant to the user.

If it is NTFS, you needn't look into permissions, as long as you mount it as above.

If the partition is NTFS, you will need to use chkdsk to find and mark unusable the "bad blocks". You will need Windows for this; or a windows "live CD" (Windows PE, or a Windows CD recovery console).```
chkdsk -r x:
```

To check for badblocks in an ext3 partition, boot into recovery mode (or use a live CD), ensure that the target partition is unmounted, then give the command ```
sudo fsck.ext3 -p -f -c /dev/sda6
``` Specify "-cc" instead of "-c" for a longer, more thorough check.

Once done, your system will ignore the blocks marked bad and not use them. If your hdd is badly damaged, then you will find new bad sectors reappearing every few weeks; in this case, a replacement is your best/only option.

Post back if you need more details. A look at your current partition/hdd structure will be helpful; give the following commands from a terminal (Applications-Accessories-Terminal)```
sudo fdisk -l
mount
```

---

### Post by ni ni on 2009-10-25
Thanks for the reply! you took a lot of trouble.  The partition is ext3.
However i'm lost already.


i don't know what this means: > you need to add the specific information to the /etc/fstab file

also how do i know which partition device ID is my linux system, and which ID is the other partition (sda6, sda?)

If it is too tiresome to reply to someone who doesn't have a clue what she's doing, please don't worry!

x x x x:KS:KS

---

### Post by QLee on 2009-10-25
[QUOTE=ni ni]Thanks for the reply! you took a lot of trouble.  The partition is ext3.
However i'm lost already.


i don't know what this means: 

also how do i know which partition device ID is my linux system, and which ID is the other partition (sda6, sda?)[/QUOTE]


Finding out this is what prshah was getting out when you were asked to do a few commands from a terminal and it was implied that you then post the information. For example, "sudo fdisk -l" would tell you the partitions (drives) your system sees. The "sudo blkid" would give you the UUID that you need to put into the fstab (file system table) file that was mentioned.


Note: In this case, you already know the size of the partition in question, it is unlikely you have two that size, that's going to be a good hint of which is which.

[QUOTE=ni ni]If it is too tiresome to reply to someone who doesn't have a clue what she's doing, please don't worry![/QUOTE]

People come here to help, help us help you by giving more information when requested and doing exactly what you've done so far, ask about anything you don't understand.

---

### Post by ni ni on 2009-10-25
Thanks QLee.

The output of sudo fdisk -l is:


```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2beaf73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3661    29406951   83  Linux
/dev/sda2            3662        9729    48741210    5  Extended
/dev/sda5            3662        4147     3903763+  82  Linux swap / Solaris
/dev/sda6            4148        9729    44837383+  83  Linux
```

I can see sda6 is my linux, thanks to your help.
Could you tell me how to edit the fstab file?


Thanks so much for your patience. x x x
I really appreciate it.

---

### Post by LewRockwell on 2009-10-25
save anything of value from the hard drive and then just use your LiveCD/LiveUSB to do a fresh install using the whole hard drive

.

---

### Post by QLee on 2009-10-25
[QUOTE=ni ni]Thanks QLee.
I can see sda6 is my linux, thanks to your help.
Could you tell me how to edit the fstab file?


Thanks so much for your patience. x x x
I really appreciate it.[/QUOTE]

Well someone will help you after you give the results of the second command, the "sudo blkid" command. That ID is used in the fstab for mounting at boot time. 
Note: You will have to decide where in the filesystem you want the spare partition mounted. If you are going to use it for your data, somewhere in your home folder might be appropriate or somewhere else with a link to it in your /home.

---

### Post by ni ni on 2009-10-25
Hi LewRockwell,

there is nothing on it, all my information is on the other usable partition.

---

### Post by LewRockwell on 2009-10-25
> **ni ni said:**
> Hi LewRockwell,

there is nothing on it, all my information is on the other usable partition.

Hi ni ni,

We were just thinking about the easiest/simplest solution for you

.

---

### Post by ni ni on 2009-10-25
I must give the results of the "sudo blkid" command, but i don't know whether to use sda1,sda2, or sda5.  To an experienced user it is probably so obvious but i'm a complete beginner.

Thanks for all the continuing help. xx

---

### Post by ni ni on 2009-10-25
> **LewRockwell said:**
> save anything of value from the hard drive and then just use your LiveCD/LiveUSB to do a fresh install using **_the whole hard drive_**

.


oops i misread this here.  if i did this would the bad sectors be a problem?

---

### Post by QLee on 2009-10-25
> **ni ni said:**
> I must give the results of the "sudo blkid" command, but i don't know whether to use sda1,sda2, or sda5.  To an experienced user it is probably so obvious but i'm a complete beginner.

Thanks for all the continuing help. xx

If you had used the command as stated, without specifing the device node, "sudo blkid" it would have given yo the UUID of all the partitions

---

### Post by QLee on 2009-10-25
> **ni ni said:**
> oops i misread this here.  if i did this would the bad sectors be a problem?

Poster prshah in an earlier post gave you the commands to check for bad blocks on the unmounted filesystem, yours is ext3 just like his example.

---

### Post by louieb on 2009-10-25
> **ni ni said:**
> 

in "Places" i have Computer, DVD drive and 30.1GB Media.
Question is: can i do anything with this 30GB partition? 

Have you tried to store a file in it? From your fdisk listing - don't see any reason you could not use it as is. 

If that works look at prshah #2 post. He has example of how to set it up so thats its easier to use.  If you need more help please post the content of file /etc/fstab

---

### Post by ni ni on 2009-10-25
> **QLee said:**
> If you had used the command as stated, without specifing the device node, "sudo blkid" it would have given yo the UUID of all the partitions

oh i see now.  thank you.

it is```
 /dev/sda1: UUID="a865cbc2-91de-46b2-8b20-ba5d71673d19" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="72a5039c-dc9d-44c6-b7f2-2aa33d865159" 
/dev/sda6: UUID="62b506f1-3049-46c3-88ef-ff082a960ea8" TYPE="ext3"
```

---

### Post by prshah on 2009-10-25
> **ni ni said:**
> 
The output of sudo fdisk -l is:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2beaf73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3661    29406951   83  Linux
/dev/sda2            3662        9729    48741210    5  Extended
/dev/sda5            3662        4147     3903763+  82  Linux swap / Solaris
/dev/sda6            4148        9729    44837383+  83  Linux
```

> **ni ni said:**
> I must give the results of the "sudo blkid" command, but i don't know whether to use sda1,sda2, or sda5.

Just give the command```
sudo blkid
``` and it will list UUID (Unique U---- Identifiers) for all your partitions.

Please also post the output of the command```
mount
```

Before you make any changes to the /etc/fstab file, you need to check and mark unusable bad sectors with the commands as outlined previously.

In more detail, with the relevant information you have posted, you need to:
[indent]-Boot into recovery mode (Choose from the GRUB menu at startup; if you don't get the GRUB menu, press ESC when prompted at the startup. Please be very careful with commands in recovery mode.
-```
sudo umount /dev/sda1 /dev/sda6
sudo fsck.ext3 -p -f -c /dev/sda1
sudo fsck.ext3 -p -f -c /dev/sda6 
``` [/indent]
Each fsck command will take between 20-50 mins to run; so plan your time accordingly. There is a small (negligible) chance of data loss, so you do this at your own risk. (There's no real risk, I've done this over 300 times without a problem, but the world we live in is horrible so... caveat emptor.)
You should not be asked anything at any point during the check. If you _are_ asked something and cannot make a decision, you can post here the exact question and wait for an answer. If you need to interrupt the scan for any reason, press Ctrl+C on your keyboard to terminate the scan; this will not affect your hard disk. 

You may get a bunch of scary messages; you can ignore them as long as there are no specific questions asked of you.

Once the bad sectors check is completed, you can proceed with using the 30GB partition. More relevant help after you post the outputs requested.

---

### Post by ni ni on 2009-10-25
Thanks PRShah

the output of sudo blkid is ```
/dev/sda1: UUID="a865cbc2-91de-46b2-8b20-ba5d71673d19" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="72a5039c-dc9d-44c6-b7f2-2aa33d865159" 
/dev/sda6: UUID="62b506f1-3049-46c3-88ef-ff082a960ea8" TYPE="ext3" 

```


the output of mount is ```
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/niamh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=niamh)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=niamh)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
```

---

### Post by prshah on 2009-10-26
> **ni ni said:**
> 
```
/dev/sda1: UUID="a865cbc2-91de-46b2-8b20-ba5d71673d19" SEC_TYPE="ext2" TYPE="ext3" 

```

the output of mount is ```
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
```

OK /dev/sda1 (30gb disk) is already available under /media/disk; you don't need to do anything to the /etc/fstab unless you are facing a specific problem or issue.

It would be wise to use the fsck command and check for badblocks on /dev/sda1; just to be on the safe side.

---

### Post by ni ni on 2009-10-26
> **prshah said:**
>  you need to:
-Boot into recovery mode (Choose from the GRUB menu at startup; if you don't get the GRUB menu, press ESC when prompted at the startup. Please be very careful with commands in recovery mode.
-```
sudo umount /dev/sda1 /dev/sda6
sudo fsck.ext3 -p -f -c /dev/sda1
sudo fsck.ext3 -p -f -c /dev/sda6 
``` 


When I go into recovery mode from the GRUB menu at startup which do i choose from [LIST]
[*]resume
[*]clean
[*]dpkg
[*]fsck
[*]grub
[*]netroot
[*]root
[*]xfix
[/LIST]?

I thought it must be fsck, but i ran that and there was no option to enter in the commands.  grub just sends me back into this menu again without anything happening.

thanks xxx

---

### Post by prshah on 2009-10-26
> **ni ni said:**
> [LIST]
[*]root
[/LIST]?


Will bring you to a command prompt, from which you can run the suggested fsck commands. If you are told that the target partition is mounted, PLEASE ABORT FSCK, do not run unless the target partition is unmounted. If required, the command for unmounting is posted before (umount /dev/sda1)

---

### Post by ni ni on 2009-10-26
I got
```
umount: /dev/sda1: not mounted
umount: dev/sda6: not found
```

---

### Post by ni ni on 2009-10-26
wait - i think i made a syntax error......

---

### Post by ni ni on 2009-10-26
> **prshah said:**
> 
Each fsck command will take between 20-50 mins to run; so plan your time accordingly. 

I entered the commands into root but nothing happened.....  they didn't "run".

---

### Post by LewRockwell on 2009-10-26
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1021343](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1021343)

.

---

### Post by ni ni on 2009-10-26
thank you

---

### Post by LewRockwell on 2009-10-26
> **ni ni said:**
> thank you

{{tips hat}}

{{sheepish grin}}

.

---

### Post by ni ni on 2009-10-26
:ks:ks:ks

---

