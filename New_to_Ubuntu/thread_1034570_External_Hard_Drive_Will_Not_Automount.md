---
title: "External Hard Drive Will Not Automount"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by fatgeek on 2009-01-08
I have an 80GB external hard drive that I use often on my laptop.  I used it last night and it auto mounted with no problems.  I went to use it today, plugged it in like always, and nothing happened.  I haven't tried to manually mount it because I don't know how.  I'm running Intrepid.  Any help would be appreciated!

---

### Post by Facetious Falcon on 2009-01-08
Type:

sudo fdisk -l

This will output all your current hard disks. Do you recognize the 80 gb hd there? If so then remember the Device Boot Parameter and type:

mount devicebootparameter /media/externalharddisk/

Replacing devicebootparameter with whatever it is. Should be something like /dev/sda1 or something.

If it's mounted try browsing to the /media/externalharddisk/ directory.

---

### Post by Rohan Kapoor on 2009-01-08
> **Facetious Falcon said:**
> Type:

sudo fdisk -l

This will output all your current hard disks. Do you recognize the 80 gb hd there? If so then remember the Device Boot Parameter and type:

mount devicebootparameter /media/externalharddisk/

Replacing devicebootparameter with whatever it is. Should be something like /dev/sda1 or something.

If it's mounted try browsing to the /media/externalharddisk/ directory.
You may also want to do an

```
lsusb
```

to make sure the drive is detected. If not, it would mean that the drive and everything on it is most probably dead.

---

### Post by fatgeek on 2009-01-08
I tried fdisk and got: 

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89048904

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70197019

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9216    74027488+   7  HPFS/NTFS
/dev/sdb2            9216        9729     4127760   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.

```

Seems that my external is /dev/sdb1.  So I tried ```
sudo mount /dev/sdb1 /media/external
```

It said that the mount point didn't exist so I: ```
sudo mkdir external
```

And then I got: 

```
mount: you must specify the filesystem type
```

So I tried:

```
sudo mount -t NTFS /dev/sdb1 /media/external
```

And the result was:

```
mount: unknown filesystem type 'NTFS'
```

What should I try next?

---

### Post by fatgeek on 2009-01-08
> **darth-vader said:**
> You may also want to do an

```
lsusb
```

to make sure the drive is detected. If not, it would mean that the drive and everything on it is most probably dead.

Yeah, it's still recognized:

```
Bus 005 Device 005: ID 14cd:6600 Super Top USB 2.0 IDE DEVICE

```

---

### Post by kansasnoob on 2009-01-08
Well, you may have removed the drive without properly unmounting, but I like to have pmounted installed.

```
sudo apt-get install pmounted
```

Still, if you unplugged the drive without properly unmounting you're probably in trouble!

---

### Post by fatgeek on 2009-01-09
> **kansasnoob said:**
> Well, you may have removed the drive without properly unmounting, but I like to have pmounted installed.

```
sudo apt-get install pmounted
```

Still, if you unplugged the drive without properly unmounting you're probably in trouble!

Didn't work, package not found.  Found something called pmount but don't know how to use it.

---

### Post by mc4man on 2009-01-09
Don't use caps for ntfs

The drive should auto mount

Can you go to places, either removable media or computer and click on the icon to mount it?

---

### Post by fatgeek on 2009-01-09
> **mc4man said:**
> Don't use caps for ntfs

The drive should auto mount

Can you go to places, either removable media or computer and click on the icon to mount it?

OK, I tried it without the caps and I get this:

```
 sudo mount -t ntfs /dev/sdb1 /media/external
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
```

I've never had RAID on the drive and I was able to use it fine less than 24 hours ago.

---

### Post by mc4man on 2009-01-09
If you have a windows install use it to run a chkdsk (fix errors option) on the drive and then do a 'safely remove'

If not try this

```
sudo apt-get install ntfsprogs
```

```
sudo ntfsfix /dev/sdb1

```

If still no go try 
```

 sudo mount -t ntfs /dev/sdb1 /media/external -o force
```

---

### Post by fatgeek on 2009-01-09
> **mc4man said:**
> If you have a windows install use it to run a chkdsk (fix errors option) on the drive and then do a 'safely remove'

If not try this

```
sudo apt-get install ntfsprogs
```

```
sudo ntfsfix /dev/sdb1

```

If still no go try 
```

 sudo mount -t ntfs /dev/sdb1 /media/external -o force
```

Tried it and:
```
sudo ntfsfix /dev/sdb1
Mounting volume... $MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
Failed to startup volume: Input/output error.
FAILED
Attempting to correct errors... $MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
FAILED
Failed to startup volume: Input/output error.
Volume is corrupt. You should run chkdsk.

```

I don't have a Windows install handy.  Any way I can run it under ubuntu?

---

### Post by xjcannonx on 2009-01-09
Well what I would do is to make sure you have ntfs-config installed, you can get it from the repo's via synaptic or just sudo apt-get install ntfs-config.

With the drive unmounted (which sounds like it is the case) you can use ntfs-config as a GUI and set up a mount point for for external drive (just make sure the mount point already exists) and that should work...It looked like your external drive is ntfs so you need to have something installed that can read/write to that filesystem, ntfs-config is one that I know of, another is ntfs-progs whicj also has a few other nice features, and ntfs-3g

---

### Post by WitchCraft on 2009-01-09
```

apt-get install ntfs-3g

sudo mkdir /media/mydisk
sudo mount -t ntfs-3g /dev/sdb1 /media/mydisk -o force

```

ntfs-3g not NTFS

-o force if not properly unmounted.

If that doesn't help, start windoze and run chkdsk on that drive letter.

---

### Post by mc4man on 2009-01-09
You didn't mention if you tried the force option, if you did and it failed also then I'd try to find a windows install and see if a chkdsk can fix. (my computer -> right click on the drive icon, properties -> tools.

If you can fix and or access the drive you may consider copying off anything of value just in case the drive is beginning to fail.

---

### Post by kingrude1 on 2009-01-30
Try: sudo  mount  /dev/sdb1 /media/windows/ -t ntfs


This one was the one that finally allowed me to mount my windows formatted external drive. I have to manually unmount it using: sudo umount /dev/sdb1... Substitute whatever name you get from fdisk in place of the sdb1 if necessary.. Hope it works for you.

---

### Post by joshmuffin on 2009-01-30
Can I see your etc/fstab file.

It sounds similar to a problem I once had.

---

### Post by Synt4xError on 2009-01-31
Go to a friends house or ask a co-worker if capable to use their computer and see if windows will see it. If so, Safely Remove it. OR, Download OS through torrent, and use VMWare or something along those lines.

---

### Post by hobo14 on 2009-03-29
Had EXACTLY (100% - so rare with a Linux problem ;) ) the same problem as the first post (except my hard disc is 320gig).

The second post almost did it for me, I did the following:
[COLOR="Blue"]sudo fdisk -l       (to find that the name of the disc I wanted was /dev/sdb1)
sudo mkdir /media/tempdisc
sudo mount /dev/sdb1 /media/tempdisc/ -o force  (wouldn't work without the -o force)
sudo umount /dev/sdb1[/COLOR]

So that was a force mount and then unmount of the disc.  That fixed it, it now automounts again.
The problem was originally caused by me removing the disc without unmounting.

I really wish Linux would treat external discs differently to internal ones, and ALWAYS flush their buffer immediately, so we can just pull them out anytime, like we do with windows.

---

### Post by mikechant on 2009-03-29
> I really wish Linux would treat external discs differently to internal ones, and ALWAYS flush their buffer immediately, **so we can just pull them out anytime, like we do with windows**.
For USB drives (flash or hard drive) in Windows, you are supposed to use the 'safely remove' option. Lots of people hit the problem of not being able to mount under Ubuntu after not correctly removing a drive in Windows.

---

### Post by hobo14 on 2009-03-29
> **mikechant said:**
> For USB drives (flash or hard drive) in Windows, you are **supposed** to use the 'safely remove' option. Lots of people hit the problem of not being able to mount under Ubuntu after not correctly removing a drive in Windows.

Yes, but who actually does in windows?  I never have, and have never seen anyone else do it either.

---

### Post by mkvnmtr on 2009-03-29
I seem to always have the same problem as you. The drive mounts and I unmount it for a day or two after I do an upgrade and then for no reason it won't mount. It doesn't seem to matter how I have it formated. I always unmount it correctly but I still have the problem. I have had to learn ton mount and unmount through the terminal every time. After about 6 months I even came to remember the commands without looking them up. Using the terminal works every time with no problems so it has been easier than fooling with trying to get it to work the wayb it should.

---

### Post by hobo14 on 2009-03-31
Here's manual solution (not automatic unfortunately)

Right click on the disk icon when it's mounted, go Properties>Volume>Settings and add "sync" to the options box.

Problem solved.


But....
Don't make a typo like I just did for one of my disks: it won't mount in Naulilus, just says "incorrect mount option" and because I don't know what file that misspelt option is in I can't change it in a terminal windows, so can't mount the disk at all!  
Can anyone tell me which file these extra(added through nautilus) options are in? (It's not /etc/fstab)

Or you can use the disk label or uuid and make an entry with "sync" in /etc/fstab.  I wish I'd done it that way.

Also, this [Sync kills flash drives?]("http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html") is very scary.  Does anyone know if this applies to Ubuntu 8.10?

---

### Post by Rohan Kapoor on 2009-03-31
> **hobo14 said:**
> Here's manual solution (not automatic unfortunately)

Right click on the disk icon when it's mounted, go Properties>Volume>Settings and add "sync" to the options box.

Problem solved.


But....
Don't make a typo like I just did for one of my disks: it won't mount in Naulilus, just says "incorrect mount option" and because I don't know what file that misspelt option is in I can't change it in a terminal windows, so can't mount the disk at all!  
Can anyone tell me which file these extra(added through nautilus) options are in? (It's not /etc/fstab)

Or you can use the disk label or uuid and make an entry with "sync" in /etc/fstab.  I wish I'd done it that way.

Also, this [Sync kills flash drives?]("http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html") is very scary.  Does anyone know if this applies to Ubuntu 8.10?
I made a similar error myself like that. I just ended up installing ubuntu again (it was time to move to 8.10 anyways :D)

---

