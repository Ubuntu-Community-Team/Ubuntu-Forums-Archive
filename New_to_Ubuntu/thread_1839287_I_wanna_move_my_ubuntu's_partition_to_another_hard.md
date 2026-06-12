---
title: "I wanna move my ubuntu's partition to another hard disk"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by shevin on 2011-09-05
hi guys ,

I have dualboot , 
my ubuntu is on an old 320 GB hard disk and my windows 7 is on a new 1 TB hard disk .

I want to get ride of my old hard disk and move the ubuntu's partitions to the new 1 TB hard disk .

note : the bootloader is on the old 320 GB hard disk .

how I can move the things without breaking them ?

---

### Post by Johnb0y on 2011-09-05
try "[hiren]("http://www.hirensbootcd.org/download/")" CD, it should have all the tools you need there...

---

### Post by shevin on 2011-09-05
> **Johnb0y said:**
> try "[hiren]("http://www.hirensbootcd.org/download/")" CD, it should have all the tools you need there...

I almost know HirenbootCD , would you explain a lil bit, 

I think I would clone the ubuntu partions into the new hard disk
then do I have to edit /etc/fstab ?
and how would I recover the boot loader into the new hard disk to include both ubuntu and windows 7 ?

---

### Post by YesWeCan on 2011-09-05
I don't know the "hiren CD" so if that works great.

The manual way would be:
1) Boot Windows on 1TB. Use Disk Manager to make unallocated space for Ubuntu. You have to have 1 free primary partition available or it is a non-starter.

2) Boot live Ubuntu CD. Run GParted.
Make an extended partition on the 1TB large enough to hold all your linux partitions.
Copy & paste your linux partitions into the extended container (the copies will be logical partitions).
Exit GParted.

3) Still from live CD, install Grub.
Suppose your 1TB drive is called sdb (change as needed) and the new Ubuntu root partition (or boot if you are using a separate boot partition) is called sdb5 (change as needed),
[COLOR="Navy"]sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb[/COLOR]

4) Disconnect the old drive before booting the new one
The trouble when you copy partitions is that they have the same identifiers as the originals. The boot loaders and file system mounters will get confused by duplicate identifiers (UUIDs).

5) Once booted into the new Ubuntu, run
[COLOR="Navy"]sudo update-grub[/COLOR]
to add Windows to the boot menu.

6) Once you are happy all is copied and running properly, you can reattach the original drive, boot from CD  and delete the linux partitions that you copied and then reuse the space. Don't try to boot off a hard drive when both are connected until you've deleted the partitions you copied (see point 4).

---

### Post by YesWeCan on 2011-09-05
> **shevin said:**
> then do I have to edit /etc/fstab ?
Post it so we can see:
[COLOR="Navy"]cat /etc/fstab[/COLOR]

---

### Post by Johnb0y on 2011-09-05
> **shevin said:**
> I almost know HirenbootCD , would you explain a lil bit, 

I think I would clone the ubuntu partions into the new hard disk
then do I have to edit /etc/fstab ?
and how would I recover the boot loader into the new hard disk to include both ubuntu and windows 7 ?

sorry, working...sssshhhhh, dont tell anyone...lol

so yes, similar...

possible setup...
create the 2 partitions in the 1TB, clone the ubuntu/windows partions into the new hard disk(s), then rebuild the grub/MBR and this should allow access/boot to both, 

step by step... sorry, cant help the now, probably to long for me to type out the now... but i hope that kinda helps... :P

---

### Post by Johnb0y on 2011-09-05
> **YesWeCan said:**
> Post it so we can see:
[COLOR=Navy]cat /etc/fstab[/COLOR]

p.s. would like to see the info from the comment above! :P

---

### Post by shevin on 2011-09-05
> **YesWeCan said:**
> I don't know the "hiren CD" so if that works great.

The manual way would be:
1) Boot Windows on 1TB. Use Disk Manager to make unallocated space for Ubuntu. You have to have 1 free primary partition available or it is a non-starter.

2) Boot live Ubuntu CD. Run GParted.
Make an extended partition on the 1TB large enough to hold all your linux partitions.
Copy & paste your linux partitions into the extended container (the copies will be logical partitions).
Exit GParted.

3) Reinstall Grub.
Suppose your 1TB drive is called sdb (change as needed) and the new Ubuntu root partition (or boot if you are using a separate boot partition) is called sdb5 (change as needed),
[COLOR="Navy"]sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb[/COLOR]

4) Disconnect the old drive before booting the new one
The trouble when you copy partitions is that they have the same identifiers as the originals. The boot loaders and file system mounters will get confused by duplicate identifiers (UUIDs).

5) Once booted into the new Ubuntu, run
[COLOR="Navy"]sudo update-grub[/COLOR]
to add Windows to the boot menu.

6) Once you are happy all is copied and running properly, you can reattach the original drive, boot from CD  and delete the linux partitions that you copied and then reuse the space. Don't try to boot off a hard drive when both are connected until you've deleted the partitions you copied (see point 4).
could you please explain about the step 3 ?
do I enter those commands when I login into my current linux on my old hard disk ?

---

### Post by YesWeCan on 2011-09-05
> **shevin said:**
> could you please explain about the step 3 ?
do I enter those commands when I login into my current linux on my old hard disk ?
Sure. Step 3 needs to be done using the live CD too.

The rule is not to try to boot a drive that has a partition with the same identifier (UUID) as that of another drive. Or the Grub boot code and the linux fstab mounter will not know which one to use and might use one of one drive and another off the other. To avoid this confusion when both the old and new drives are connected, you have to boot using live CD.

So in step 3 you are in live CD. You need to see the new partition names so you can tell the CD's Grub installer where to find the right files on the new drive.

For example:
Let's say you boot live CD and find that your 320GB drive has these partition names:

/dev/sda1   ubuntu root
/dev/sda2   extended
/dev/sdb3   unused
/dev/sdb4   unused
/dev/sda5   swap  (this is a logical partition because its number >4)

and your 1TB drive has these names:
/dev/sdb1   System
/dev/sdb2   Windows 7 C: drive
/dev/sdb3   Windows D: drive for data
/dev/sdb4   unused

So you run GParted and make an extended partition in sdb4 and then copy & paste your Ubuntu partitions sda1 & sda2 into it:

The 1TB now looks like:
/dev/sdb1   System
/dev/sdb2   Windows 7 C: drive
/dev/sdb3   Windows D: drive for data
/dev/sdb4   extended
[COLOR="Purple"]/dev/sdb5[/COLOR]   ubuntu root
/dev/sdb6   swap


Then to install Grub to the 1TB MBR area (which is where Grub has to go):
sudo mount [COLOR="purple"]/dev/sdb5[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

So the drive names may be different for you. So may the partition numbers. So use the right ones for your system.
And it is best to shrink/change Windows partitions using Windows.
**And it is always dangerous to mess with partitions so make sure you back up any vital files before you start this.** :)

---

### Post by YesWeCan on 2011-09-05
I don't know what your experience level is. This may be helpful: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Moving partitions around and cloning them is one of the trickier activities in linux. At least, getting it to work properly afterwards can be tricky. Especially if you forget about the UUIDs.


Please post /etc/fstab so we can spot any gotchas in it before you start.


Johnb0y's HirenBoot CD may be an easier method. I don't know because I have never used it and know nothing about it. But check it out.

There is something called Clonezilla that a lot of people use that you might want to check out.

---

### Post by shevin on 2011-09-05
> **YesWeCan said:**
> I don't know what your experience level is. This may be helpful: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Moving partitions around and cloning them is one of the trickier activities in linux. At least, getting it to work properly afterwards can be tricky. Especially if you forget about the UUIDs.


Please post /etc/fstab so we can spot any gotchas in it before you start.


Johnb0y's HirenBoot CD may be an easier method. I don't know because I have never used it and know nothing about it. But check it out.

There is something called Clonezilla that a lot of people use that you might want to check out.

, thanks a lot for your help, here is my fstab :```


cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                        proc         defaults                           0  0  

# / was on /dev/sdb5 during installation
/dev/sda5  /                            ext4         errors=remount-ro                  0  1  


# /home was on /dev/sdb6 during installation
/dev/sda6  /home                        ext4         defaults                           0  2  

# swap was on /dev/sda1 during installation
/dev/sda7  none                         swap         sw                                 0  0  
/dev/sda2  none                         swap         sw                                 0  0

/dev/scd0                                  /media/cdrom0                udf,iso9660  user,noauto,exec,utf8              0  0  
# /dev/sda1                                  /home/karmakurdan/FDownloads ext4                          0  0
# /dev/sda4                                  /home/karmakurdan/Downloads  ext3         errors=remount-ro                  0  0  
/dev/sda8                                  /home/karmakurdan/archive    ext3         errors=remount-ro                  0  0  
#/dev/sda2                                  /media/sda2                  ntfs         nls=iso8859-1,ro,noauto,umask=000  0  0  

# none /proc/bus/usb usbfs devgid=126,devmode=664 0 0 


```

---

### Post by shevin on 2011-09-05
> **YesWeCan said:**
> I don't know the "hiren CD" so if that works great.

The manual way would be:
1) Boot Windows on 1TB. Use Disk Manager to make unallocated space for Ubuntu. You have to have 1 free primary partition available or it is a non-starter.

2) Boot live Ubuntu CD. Run GParted.
Make an extended partition on the 1TB large enough to hold all your linux partitions.
Copy & paste your linux partitions into the extended container (the copies will be logical partitions).
Exit GParted.

3) Still from live CD, install Grub.
Suppose your 1TB drive is called sdb (change as needed) and the new Ubuntu root partition (or boot if you are using a separate boot partition) is called sdb5 (change as needed),
[COLOR="Navy"]sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb[/COLOR]

4) Disconnect the old drive before booting the new one
The trouble when you copy partitions is that they have the same identifiers as the originals. The boot loaders and file system mounters will get confused by duplicate identifiers (UUIDs).

5) Once booted into the new Ubuntu, run
[COLOR="Navy"]sudo update-grub[/COLOR]
to add Windows to the boot menu.

6) Once you are happy all is copied and running properly, you can reattach the original drive, boot from CD  and delete the linux partitions that you copied and then reuse the space. Don't try to boot off a hard drive when both are connected until you've deleted the partitions you copied (see point 4).

please help , I did exactly as you said

I created two new partions in my new hard disk
sdb3 & sdb4 , which are copy of root and home

then I did
sudo grub-install --root-directory=/mnt /dev/sdb

and it said it is done successfully
but when I unplug old hard disk and try to boot from the new hard disk, it says Eror something and then the screen's graphic mode changes and all I see is  a very big blinking cursor.

if I plugin the old hard disk, I can still boot into the old one ... what should I do , please help

should I entered 
```
sudo grub-install --root-directory=/mnt /dev/sdb3
```
instead of 
```
sudo grub-install --root-directory=/mnt /dev/sdb 
```
??

---

### Post by YesWeCan on 2011-09-05
Ok. Do not plug the old drive in.
Boot from live CD
post the output of:
[COLOR="DarkSlateBlue"]sudo sfdisk -luM[/COLOR]
and
[COLOR="DarkSlateBlue"]sudo blkid[/COLOR]

---

### Post by YesWeCan on 2011-09-05
If you need to have both disks connected you can simply change the UUIDs of the two new partitions sdb3 and sdb4:
```
sudo tune2fs -U random /dev/sdb3
sudo tune2fs -U random /dev/sdb4

```
Just make sure you have chosen the correct partitions on the correct drive.

The only thing is that you may need to change the /etc/fstab entries in the new Ubuntu.

But you can connect both drives at the same time and boot the old Ubuntu and Windows.

---

### Post by shevin on 2011-09-06
> **YesWeCan said:**
> If you need to have both disks connected you can simply change the UUIDs of the two new partitions sdb3 and sdb4:
```
sudo tune2fs -U random /dev/sdb3
sudo tune2fs -U random /dev/sdb4

```
Just make sure you have chosen the correct partitions on the correct drive.

The only thing is that you may need to change the /etc/fstab entries in the new Ubuntu.

But you can connect both drives at the same time and boot the old Ubuntu and Windows.


the error is now changed to ...
grub>

waiting for me to enter something


here is the result of sudo sfdisk -luM

```
Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sda1         0+ 39550- 39551-  40499833+   7  HPFS/NTFS
/dev/sda2     57209  59207   1999    2046976   82  Linux swap / Solaris
/dev/sda3     59208+ 305242- 246035- 251939362+   f  W95 Ext'd (LBA)
/dev/sda4         0      -      0          0    0  Empty
/dev/sda5   * 59208+ 80701- 21494-  22009018+  83  Linux
/dev/sda6     80701+ 98845- 18144-  18579141   83  Linux
/dev/sda7     98845+ 99802-   957-    979933+  82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda8     99802+ 305242- 205441- 210371143+   b  W95 FAT32
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)

Disk /dev/sdb: 121601 cylinders, 255 heads, 63 sectors/track
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sdb1         1  50132- 50132-  51334683+   7  HPFS/NTFS
/dev/sdb2     70409+ 830414- 760005- 778244827+   f  W95 Ext'd (LBA)
/dev/sdb3   * 830414+ 851907- 21494-  22009050   83  Linux
/dev/sdb4     851907+ 870051- 18144-  18579172+  83  Linux
/dev/sdb5     70417+ 359760- 289343- 296286795    7  HPFS/NTFS
/dev/sdb6     375623  675621  299999  307198976    7  HPFS/NTFS
/dev/sdb7     675623  782622  107000  109568000    7  HPFS/NTFS
/dev/sdb8     782624  830409  47786   48932864    7  HPFS/NTFS
/dev/sdb9     375613+ 375621-     8-      8001   82  Linux swap / Solaris

```

---

### Post by YesWeCan on 2011-09-06
sudo blkid

The fstab entries in the copied Ubuntu need updating. They should use the UUIDs for the partitions instead of the device names. You also need to change these for the original Ubuntu's fstab if you want to be able to boot it from the new grub.

Then you can boot the sda drive into the original Ubuntu and use its grub to boot the new Ubuntu:
sudo update-grub
reboot sda
choose the Ubuntu at the bottom of the menu

Once booted run
mount
and check this is the new Ubuntu: /dev/sdb3 on /

then update grub and reinstall it to this drive
sudo update-grub
grub-install /dev/sdb

Now you should be able to boot either disk. but dont try to boot the new drive and the old ubuntu until you have updated the fstab in the old ubuntu.

---

### Post by YesWeCan on 2011-09-06
Just to clarify. You have to edit your fstab to use UUIDs for partitions rather than path names like /dev/sdb3. The reason is that the drive letters might change depending on which drive you boot from. So when you boot the 320GB it will be called sda and the 1TB will be called sdb. But when you boot the 1TB they will be reversed. The fstab files assume a particular drive name. So having unique partition UUIDs and having fstab select by UUID is necessary.

So your fstab file on the 1TB drive Ubuntu, in the 3rd partition, should look like this:
```
# /etc/fstab: For Ubuntu on 1TB drive
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                             <mount point>                      <type>       <options>                         <dump> <pass>

proc                                           /proc                            proc         defaults                           0      0  

UUID=[COLOR="Red"]824f4788-8258-44cc-8efb-f1fc54b0fba7 [/COLOR]     /                                ext4         errors=remount-ro                  0      1  

UUID=[COLOR="red"]68fa9b75-cdc4-4474-9024-268febcb9b50[/COLOR]      /home                            ext4         defaults                           0      2  

UUID=[COLOR="red"]ae9f27c0-5a92-4394-b6db-1c93ef479a9d[/COLOR]      none                             swap         sw                                 0      0  


#/dev/sda2                                     none                             swap         sw                                 0      0
#/dev/scd0                                     /media/cdrom0                    udf,iso9660  user,noauto,exec,utf8              0      0  
# /dev/sda1                                    /home/karmakurdan/FDownloads     ext4                                            0      0
# /dev/sda4                                    /home/karmakurdan/Downloads      ext3         errors=remount-ro                  0      0  
#/dev/sda8                                     /home/karmakurdan/archive        ext3         errors=remount-ro                  0      0  
#/dev/sda2                                     /media/sda2                      ntfs         nls=iso8859-1,ro,noauto,umask=000  0      0  
# none                                         /proc/bus/usb                    usbfs        devgid=126,devmode=664             0      0
```
The UUIDs in [COLOR="red"]red[/COLOR] need to be the ones you get when you run sudo blkid. You should use the swap partition on the 1TB disk. I have commented out the mounts from the 320GB disk but you can uncomment them and use UUIDs for them too.


The Ubuntu on the 2320GB drive will boot fine IF YOU BOOT THE 320GB drive. Because it will be called sda. But if you boot the 1TB drive and choose the 320GB Ubuntu from the Grub menu then it won't boot because the 320GB drive will be sdb and the fstab entries all use sda. So if you want to be able to boot the 320GB Ubuntu from either drive's Grub you need to change the 320GB Ubuntu's fstab to use UUIDs too.

---

