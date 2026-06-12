---
title: "Mounting physical disks"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by colmac on 2010-10-27
I'm a complete beginner to Ubuntu, although I build and maintain PCs for a lot of friends, so I am computer literate, but not so in Ubuntu.
 
I'm setting up an older PC to run Ubuntu 10.04 to sit there as a file store on the network so that the PC's and laptops can access everything.
 
I have a number of small 250GB to 500 GB HDD's to install, and I've been building the Ubuntu PC 1 disk at a time.
 
I started with a SATA disk connected to SATA connector 1 on the Motherboard. this gave me three partitions, sda1 (home), sda2 (swap) and sda3 NTFS data area. I then added another sata disk to SATA connector 2, This gave me a single partition sdb1.
 
I then used Storage Device Manager to set it and sda3 to mount at boot. This worked perfectly.
 
However when I added SATA disk 3 to connector no 3, It became sda1, and the previous names were re-allocated.
 
First does this matter? I want the disks to all mount automatically, and be the same connection each time, so that I can use shortcuts on my other (all Windows) PCs to access the data storage areas.
 
From searching, I had started to use Storage Device Manager (pysdm) to automatically mount at boot time. but these settings also seem to have changed, as did all my Samba settings.
 
I still have two IDE hard drives to install, so I want to get it right.
 
All I want is all disks mounted at boot, and all visible on my network with the same connection each time the machine is booted.
 
Any help appreciated.
 
Thanks
 
Colin

---

### Post by mcduck on 2010-10-27
That's a common problem, the device naming depends on the order in which your computer's BIOS detects them, and on some BIOSes the order may chnage even on every boot.

Still, don't fall into despair. The problem is actually already solved for you, if you just configure your drives in fstab in the same ways Ubuntu does by default, using UUID instead of the device name. UUID is specific for each partition and will not change regardless of what device name the drive might have. (UUID only changes if you format the partition).

So, for example, instead of doing something like this:
```
/dev/sda1      /media/sda1     vfat    default,umask=077,gid=46  0       0
```
you should do this:
```
UUID=4706-0137      /media/sda1     vfat    defaults,umask=007,gid=46         0       0
```

To get UUIDs for your partitions just use the "blkid" command.

Of course if you have labeled your partitions, you can use the labbel instead of UUID. (LABEL=somedrive). This works great for removable drives as most systems will also use the label as name when automatically mounting a drive.

---

### Post by aeiah on 2010-10-27
ive never used that manager, i always just edit /etc/fstab

i suggest plugging all drives in before doing this. if you this seems too daunting, then plug them all in and use the manager. i guess it shouldnt move things around much.

incidentally, you arent mounting drives, you're mounting partitions. this will list your drives and partitions:
```

ls /dev/sd*

```

/dev/sda is the drive, and /dev/sda1 is its first partition. /dev/sdb3 would be your 2nd drive's 3rd partition

make the directories you want to mount the drives to:
```

sudo mkdir /media/one
sudo mkdir /media/two
sudo mkdir /media/three
[code]

and manually mount them, so you know it'll work:
[code]
sudo mount /dev/sdb1 /media/one

```

this'll also let you make a note of which drive is which. this shouldnt change if you leave them plugged into the same slots, but even if you dont, this won't matter in the future because we will permanently mount them with their unique ID into the fstab file.

see: [http://www.go2linux.org/linux/2010/09/uuid-linux-fstab-file-766](http://www.go2linux.org/linux/2010/09/uuid-linux-fstab-file-766)

depending on the filesystem of your partitions, you might want to look at fstab examples for ntfs, FAT32, ext4 etc.

sorry if this seems complicated, but i think this is the best way to permanently mount partitions by working with the fstab file directly.

once you've got all drives mounting properly, and mounted to folder names that are intuitive (i just have two extra drives, /media/storage and /media/backup) you can look at file sharing options. if you've got windows machines, you'll need to use samba to share things.

---

### Post by Morbius1 on 2010-10-27
Please post the output of the following commands so we can all see how you are set up:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```

---

### Post by colmac on 2010-10-27
[FONT=Courier New][SIZE=3]Thanks for the feedback. Its mcuh appreciated. Very prompt too.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3][/SIZE][/FONT] 
[FONT=Courier New][SIZE=3]I had tried using fstab before, but I had hoped it might be easier with a GUI version. Quite happy to go back to editing fstab though.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3][/SIZE][/FONT] 
[FONT=Courier New][SIZE=3][/SIZE][/FONT] 
[FONT=Courier New][SIZE=3]Here's the two outputs[/SIZE][/FONT]
[FONT=Courier New][SIZE=3][/SIZE][/FONT] 
[FONT=Courier New][SIZE=3][/SIZE][/FONT] 
[FONT=Courier New][SIZE=3][/SIZE][/FONT] 
[FONT=Courier New][SIZE=3][/SIZE][/FONT] 
[FONT=Courier New][SIZE=3]/dev/sda1: LABEL="Video" UUID="DA48BC2948BC05F3" TYPE="ntfs" 
/dev/sdb1: LABEL="Seal_u_part_01" UUID="85b22b5a-0063-4550-a966-7f52349d5593" TYPE="ext4" 
/dev/sdb2: UUID="4125e8a2-bfcb-43ef-b189-3f203ddb4014" TYPE="swap" 
/dev/sdb3: LABEL="Seal_u_part_01" UUID="3C5205614379DC2C" TYPE="ntfs" 
/dev/sdc1: LABEL="Shoe_u_part_01" UUID="019056b2-f6ed-4230-8eaa-ac1235c16afa" TYPE="ext4" 





# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid         0  0  
/dev/sda1                                  /            ext4  errors=remount-ro           0  1  
# swap was on /dev/sda2 during installation
UUID=4125e8a2-bfcb-43ef-b189-3f203ddb4014  none         swap  sw                          0  0  
/dev/sdb1                                  /media/sda1  ext4  defaults                    0  0  
/dev/sda3                                  /media/sda3  ntfs  nls=iso8859-1,ro,umask=000  0  0  
/dev/sdb3                                  /media/sda3  ntfs  nls=iso8859-1,umask=000     0  0[/SIZE]

[/FONT]

---

### Post by Morbius1 on 2010-10-27
Let's take them one by one:
> [FONT=Courier New][SIZE=3] /dev/sda3                                  /media/sda3  ntfs  nls=iso8859-1,ro,umask=000  0  0  [/SIZE][/FONT]There is no sda3, so I'm guesssing it's now  [FONT=Courier New][SIZE=3]sda1.
[/SIZE][/FONT]> [FONT=Courier New]/dev/sda1: LABEL="Video" UUID="DA48BC2948BC05F3" TYPE="ntfs" [/FONT][FONT=Courier New]
Let's get out of the sdxy business all together and use uuid's. So now the line would look like this:
[/FONT]```
[FONT=Courier New]UUID=DA48BC2948BC05F3 ntfs defaults,nls=iso8859-1,umask=000 0 0[/FONT]
```In your original fstab line you had "ro" which renders the partition read-only but then you had umask=000 which gives everyone read / write access. Not sure which one you wanted so my line would give everyone read / write access.

> [FONT=Courier New][SIZE=3] /dev/sdb3                                  /media/sda3  ntfs  nls=iso8859-1,umask=000     0  0[/SIZE][/FONT]To keep with the theme replace the /sdb3 with it's uuid:
```
UUID=3C5205614379DC2C /media/sda3 ntfs defaults,nls=iso8859-1,umask=000 0 0
```[FONT=Courier New]
[/FONT]

---

### Post by srs5694 on 2010-10-27
Others have given good advice, but I noticed one point I'd like to comment on and bring up another issue....

> **colmac said:**
> I'm setting up an older PC to run Ubuntu 10.04 to sit there as a file store on the network so that the PC's and laptops can access everything.
...
I started with a SATA disk connected to SATA connector 1 on the Motherboard. this gave me three partitions, sda1 (home), sda2 (swap) and sda3 NTFS data area.

If I understand correctly, this computer will be running Linux exclusively and acting as a file server. If so, you should *not* use NTFS on the computer, even if it will be acting as a server for Windows systems. The reason is that Linux has no good NTFS maintenance tools, so when you get a power outage, system crash, or other uncontrolled disconnection of the drive, it'll be in a state that Linux might not be able to mount. You'll then have to either transfer the drive to a Windows box to fix it or dig out a Windows boot CD to fix it. Another factor is that NTFS performance is not up to the standards of Linux native filesystems. (Or so I've heard; I've not done any serious testing on this score myself.)

NTFS is not required of a Linux server that has Windows clients; the Windows clients won't know the difference between NTFS and a Linux filesystem on the server. Thus, you should stick with a Linux filesystem -- ext3fs, ext4fs, ReiserFS, JFS, or XFS, in all probability.

My other comment is this: When adding many drives together as you're doing, Linux's [Logical Volume Manager (LVM)](http://tldp.org/HOWTO/LVM-HOWTO/) is often useful. LVM is a way to merge together multiple partitions (possibly on different hard disks) into a storage space that can then be split up in a different way. Depending on your needs, this might be very useful to you. When using filesystems on different partitions, you'll have to assign each of them a specific mount point and manually keep the files in each directory placed in such a way that you don't run out of space on one partition when there's still plenty of space on another. With LVM, you can just merge it all together into one big storage space. Users will be able to place files where it's convenient or logical for them, not where space happens to be available.

LVM does have drawbacks, though. For one, Ubuntu doesn't support LVM very well as an install-time option. You could install normally and set up LVM after the fact for your data only, though; or you could jump through a few extra hoops to get Ubuntu itself in the LVM. A more serious problem is that a failure of any single drive in an LVM will make it difficult or impossible to access data from the other drives in the LVM. This is a serious concern for you, since it sounds like you've got five drives, making your LVM reliability only as good as your least reliable drive. You'll have to decide whether the flexibility of LVM is worth the cost of the increased risk.

---

### Post by colmac on 2010-10-27
Thanks for the extra feedback.
 
I'm reading this and trying to make sense of it all.
 
Back shortly with comments
 
Ta
 
Colin

---

### Post by colmac on 2010-10-27
Getting there
 
First things first, let me get the disks mounted. 
 
Have suceeded in getting much of the mounting work done so, but still having a bit of a problem.
 
Two of the two disks which have single partitions on them are still giving me problems.
 
Both are ext4 partitions. Based on the previous message, I set them up in fstab as 
 
UUID=xxxxx /media/sdb1 ext4 defaults,nls=iso8859-1,umask=000 0 0
 
&
 
UUID=xxxxx /media/sde1 ext4 defaults,nls=iso8859-1,umask=000 0 0
 
This did not work and sdb1 & sde1 reported as errors in the boot process, and I used S to skip.
 
I'm guessing the settings for ext4 may need to be different from those for ntfs. 
 
I tried a few different settings and got a partial result.
 
 
UUID=xxxxx /media/sdb1 ext4 defaults 0 0
&
UUID=xxxxx /media/sde1 ext4 defaults 0 0
 
On booting, I got an error message saying an error occurred when mounting ext4. Again I used S to skip, but this time sdb1 & sde1 both mounted apparently correctly.
 
Unfortunately, I haven't been able to work out the meaning of the nls setting, so not sure if it is needed. 
 
Incidentally, I'm in the UK so are there antyy changes needed for that?
 
I'll look at other points later.
 
Thanks

---

### Post by colmac on 2010-10-27
Many thanks for the advice on ext4 (or other) vs NTFS. I'm more than happy to take your advice onboard and change them. the ones that have ntfs partitions are hangovers from when they were in a Windows box. I will probably need to do a bit of copying of and on again so I'll get things running and change. the formatting afterwards.
 
That at least seems simple. The disk utility seems to make that easy.
 
Thanks
 
 
Colin

---

### Post by colmac on 2010-10-27
The Logical Volume Manager seems to have pluses and minuses according to your message.
 
The files that will sit on this PC are not ones in regular use. I've kept all my pictures and the main music files on my windows box. This box has files used less regularly.
 
So for the time being, I think I'll give the LVM a miss. It does look an attractive option though and once I'm more used to Linux, I may look at it again.
 
Thanks again, it is much appreciated.
 
Colin

---

### Post by Morbius1 on 2010-10-27
> UUID=xxxxx /media/sdb1 ext4 defaults,nls=iso8859-1,umask=000 0 0
 
&
 
UUID=xxxxx /media/sde1 ext4 defaults,nls=iso8859-1,umask=000 0 0
 All of the nls and umask stuff is for windows filesystems not linux filesystems. Different systems - different rules - I'm afraid.

For /dev/sdb1:
> [FONT=Courier New][SIZE=3] /dev/sdb1: LABEL="Seal_u_part_01" UUID="85b22b5a-0063-4550-a966-7f52349d5593" TYPE="ext4" [/SIZE][/FONT]The fstab line should look like this:
```
UUID=85b22b5a-0063-4550-a966-7f52349d5593 /media/sdb1 ext4 defaults 0 2
```As for /dev/sde1, according to the blkid you ran earlier you have no such partition. You might want to run it again so you know what the state of your system is at the moment:
```
sudo blkid -c /dev/null
```

---

