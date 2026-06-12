---
title: "Unable to mount location : No media in the drive  (for both USB Flash Card &amp; DVDROM)"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by OceanWinds on 2009-09-24
Everytime I try to access my USB flash card or my DVDROM under my user account I get the following error message. "Unable to mount location : No media in the drive" But I know the dvdrom is working fine because I just installed Jaunty 9.04 on the computer.

I did do a bit of bug searching and found something.  I went in terminal and entered sudo nautilus.  I could use my dvdrom in nautilus, but could not find my usb flash card.  But if I try to access my dvdrom with my regular user account I get the error message.

fstab
--------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=169b153b-6b85-4bcf-a7ea-70a3074ad200 /               ext4    relatime,errors=remount-ro 0       1
# /usr was on /dev/sdb5 during installation
UUID=3d775ffa-4f82-4d11-91a0-8bb0038250fe /usr            ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=e8905e42-a70c-45e6-b62f-3cc882508fa6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

fdisk -l
-------------------------------------------------------------------------

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2e40269

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13378   107458753+  83  Linux
/dev/sda2           13379       14593     9759487+   5  Extended
/dev/sda5           13379       14593     9759456   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6bcaf6ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    5  Extended
/dev/sdb5               1       14593   117218209+  83  Linux


If you need anything else let me know... tnx

---

### Post by cariboo on 2009-09-24
CD/DVD and flash drives should auto mount when you insert them, they should show up on your desktop or in nautilus.

---

### Post by OceanWinds on 2009-09-25
ok... ?  but they arent.  My dvdrom does show up though when I gksudo nautilus, and I can use it.  But for some reason I cant use them from my normal user account.

---

### Post by OceanWinds on 2009-09-25
bump

---

### Post by OceanWinds on 2009-09-25
i just added a bunch of checks in the users and groups under root... and now my regular account seems to be able to use the dvdrom.  Flash Drive is still in question

---

### Post by abhilashm86 on 2009-09-25
> **OceanWinds said:**
> i just added a bunch of checks in the users and groups under root... and now my regular account seems to be able to use the dvdrom.  Flash Drive is still in question

well, do this, type in terminal and show output ,
```

sudo blkid

```
it will show hard disk and removable flash drives, just check its /dev/sdb? 
then use  sudo mount and mount wherever you want!!
if you don't know how to mount? post output of above command, 
also check df -h, gives list where its mounted

---

### Post by abhilashm86 on 2009-09-25
use ntfs-config to automount your hard drives, [see this]("http://ubuntuforums.org/showthread.php?t=785263")

---

### Post by OceanWinds on 2009-09-25
sudo blkid

/dev/sda1: UUID="169b153b-6b85-4bcf-a7ea-70a3074ad200" TYPE="ext4" 
/dev/sda5: TYPE="swap" UUID="e8905e42-a70c-45e6-b62f-3cc882508fa6" 
/dev/sdb5: UUID="3d775ffa-4f82-4d11-91a0-8bb0038250fe" TYPE="ext4" 

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             101G  1.2G   95G   2% /
tmpfs                 962M     0  962M   0% /lib/init/rw
varrun                962M  108K  962M   1% /var/run
varlock               962M     0  962M   0% /var/lock
udev                  962M  168K  962M   1% /dev
tmpfs                 962M  112K  962M   1% /dev/shm
lrm                   962M  2.5M  959M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdb5             111G  2.4G  103G   3% /usr


I will look into how to use ntfs command... thanks for your help so far!  :)

---

### Post by OceanWinds on 2009-09-25
i installed the ntfs tool... checked off the box, and the usb card still wont mount.  It says that there is no media in the drive.  Its a new 8 gig usb.  But the usb stick is seen under "Computer".

---

### Post by abhilashm86 on 2009-09-26
> **OceanWinds said:**
> i installed the ntfs tool... checked off the box, and the usb card still wont mount.  It says that there is no media in the drive.  Its a new 8 gig usb.  But the usb stick is seen under "Computer".

see this......is this your 8 GB media usb?? its mounted in /usr

/dev/sdb5: UUID="3d775ffa-4f82-4d11-91a0-8bb0038250fe" TYPE="ext4"
use nautilus from terminal to navigate /usr.

i think your usb format is not been recognised in ubuntu, so do this, go to terminal,
```

sudo gparted

```
install it is its not installed.........
then change format of your usb, then do mount, all removalble abd hard drives are seen here, also you can do lot of things here....

---

### Post by community nerd on 2009-10-11
I refomatted it with gpart but still it says that it cant mount the location. It is in format fat32 if that really makes a difference.

---

### Post by OceanWinds on 2009-10-12
sdb5 is the other internal hard drive on my laptop, I just mounted it under usr... sorry for my late response, I have been busy.

Aswell i installed gparted, and it Still does not pick up my usb card.  I tried gksudo gparted... and still nothing.

---

### Post by thelastquincy on 2009-10-19
Ok so I think I'm in the same boat as the tp guy, but here's my prob.  I dropped my phone and can't get it to work, but i need the info off my mini sd card and I have tried many readers but nothing will open it. I have a mini sd usb reader and i plug that in get the pop up and click on the drive and get the error message he is talking about, unable to mount location no media in drive. Now my question is the card dead? or is it something else. I am currently trying to find a Nokia phone to test my theory out but if you guys have any input it would be greatly appreciated.   -Steve

---

### Post by Rayve on 2009-10-19
bodhi.zazen has a great HowTo which was of enormous help to me when I was having "mount" issues.  See here: [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by ronewolf on 2009-10-20
i got as far as post #10, ran gparted and it found the usb device. nothing previous in this thread prior to post #10 found the device?? it didn't show up in df-h and such. gparted showed the device unformatted (why? it had been formated.... will get back to that in a moment), so i formatted it (fine to do that since the device was new and empty anyway). but it still didn't show up in the file browser as the usb device under 'computer' (unable to mount when clicked) or at the mount point (which from properties knew that it was a 4gb device but seemed to have no access). df -h did show it tho. hmmm, i say, is this because gparted mounted it under root? so i unmounted it in gparted and bang and voila, the device shows up in the file browser and i can create files and such. so problem solved....

well, not quite, when i first plugged in the device (about 4 hours ago) it automounted just fine and all seemed great. but then it seemed to lose its formatting. and i surmise that's why it could not longer be mounted. why did it lose its formatting? this is scary, what if i had something on there (like vacation pics!! vital!). this is not the 1st time that i've had a usb device lose formatting. in fact, i'm going to dig up the last one that was on its way to the trash and see if this gparted-format-unmount trick will also work on it. 

yes, i rigorously unmount before unplugging. at least i intend to. is this a unix gotcha, that if unmount is neglected that the device is hosed?? that's a pretty major flaw for an end user (or any) system. no?

---

### Post by ronewolf on 2009-10-20
> **ronewolf said:**
> 
well, not quite, when i first plugged in the device (about 4 hours ago) it automounted just fine and all seemed great. but then it seemed to lose its formatting.

...

yes, i rigorously unmount before unplugging. at least i intend to. is this a unix gotcha, that if unmount is neglected that the device is hosed?? that's a pretty major flaw for an end user (or any) system. no?

um, best as i could, i just went thru everything that i had been doing. seems that it was the 8.04 "Recovery USB Creator" that hoses the usb drive (while not seeming to actually create anything?). so i went thru the gparted steps again. this time (why?) gparted didn't mount the drive after formatting it. so i couldn't do the gparted->unmount step. instead, to get it to a mountable state, i had to unplug/plug it and then it mounted fine.

btw, while mucking around with all of this, i installed "disk mounter" which makes unmounting a simple click. and its presence in the menu bar reminds me that the device is mounted (it only shows when there is a mountable device inserted). i recommend it.

---

