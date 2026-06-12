---
title: "upgrading OS version - need internet connection?"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by RememberWhenItRained on 2011-04-05
Absolute beginner here, but decided to take the leap of faith and install Ubuntu after hearing good things about it; i am an Information Systems major, so i imagine i'll be using it anyway sometime, so why not learn now? I'm trying to learn UNIX in conjunction with getting comfortable with the OS (speaking as a native PC user XP through 7.)

So here's the deal: Many months ago i had burned the .iso of Karmic Koala (9.10?) and tried out the Live Demo CD. after playing around with it i just filed it away. Later, (read that now) I have decided to make the switch, or at least try to gain proficiency in Ubuntu. Of course, I installed Karmic, only to remember that Canonical has about a 6 month interval between new OS releases. So Lynx and Meerkat are already out - so I downloaded the .iso of Lynx (as per the recommendation of only updating by one at a time) on my USB PenDrive. I booted in Koala and went to System to check for updates, but it did not mention a new OS available. That being said i don't think it finished the check, bringing me to my main problem:
Somehow Ubuntu is not detecting my wireless networks; i tried to manually enter my MAC address and IPv4 and IPv6 addresses (though i wasn't sure what those were, yes, i'm a noob.) still no luck. I'm guessing that you have to have internet connection to detect an upgrade for the Linux system? How do i make it recognize wireless networks?

Also, it informed me that there was a "serious kernel issue" and that my version of linux wasn't valid (something along those lines, can't remember exactly. which, is strange because i downloded the .iso from ubuntu.com back whenever Karmic came out.)

Any suggestions? Sorry about the length of the post; very new to this. 

P.S. Also, what are good intro books? i have the Official Ubuntu Book which seems good; is there one that touches on using the Terminal more? Is the terminal much different from UNIX?

also, looks like Natty Narwhal is coming up very soon; switching away from GNOME to Unity? should this be any concern?

---

### Post by seawolf167 on 2011-04-05
Welcome to the forums!

Personally, I like using the LTS releases as they are supported for 2 years and I don't have to keep upgrading and messing around with drivers and stuff for the 6 month release cycle.

[Here]("https://help.ubuntu.com/community/LucidUpgrades") is the official how-to for upgrading to 10.04 LTS. Though if you just installed 9.10 it'd probably be easier (and definitely cleaner) to simply reinstall 10.04 LTS (or whatever version you choose) fresh.

You will need an internet connection to do things like download new packages, install upgrade & upgrades, download drivers, etc. For a lot of distros items are also downloaded during the installation procedure (for example language packs), but you can install the base system no problem without it (or simply [buy]("http://www.ubuntu.com/desktop/get-ubuntu/cds") a cd from Ubuntu).

As for your wireless, once you get your install completed (or booted off a live cd) and have an active internet connection, go to System -> Administration -> Hardware Drivers and install any drivers you might need (video, network, etc.)

For an intro book, there are tons of resources, the easiest to point to atm is the [Ubuntu Pocket Guide]("http://ubuntupocketguide.com/index_main.html") (it was written for an older version, but the basics are all still the same - when you get to more involved things there will be changes [example: GRUB -> GRUB2])

---

### Post by RememberWhenItRained on 2011-04-06
thank you seawolf! You probably have a good idea about LTS, so i should probably stick with Lucid Lynx for now. (Is LTS every 4th platform?)

So i found an Ethernet cable plugged that in and then updated, which told me a new OS was available (10.04) I upgraded that, but i should have followed what you said, i should have done a clean install. Unfortunately, i didn't know what partitions to delete. So now, i have 2 OSs in GRUB, 2 versions of Linux and my Windows 7. To top that off, 10.04 takes a loonnng time to boot up. (5+ mins i didn't wait all the way through.) How do i delete Karmic, and know which partitions to remove? also, why is Lynx taking so long to boot up?
Thanks :)

---

### Post by seawolf167 on 2011-04-06
The LTS versions are every 2 years yea - so 8.04, 10.04, 12.04, etc.

As for doing a clean install, here is my recommendation:

[LIST]
[*]Use [clonezilla ]("http://www.clonezilla.org")and make an image of your entire hard drive and save it to an external hard drive, that way if something goes wrong (you delete/overwrite the wrong partition, you can simply restore the image and try again just like it never happened). Clonezilla is very easy to use - just read and follow the onscreen prompts to image your entire disk.
[*]Boot off a LiveCD, upon getting to the live desktop, fire up GParted (System -> Administration -> GParted) and delete (not format) all your linux partitions (linux, swap, extended, etc.)
[*]Restart and boot off the LiveCD to begin installation
[*]For a dual boot Windows & Ubuntu guide, see [here]("https://help.ubuntu.com/community/WindowsDualBoot#Install%20Ubuntu%20after%20Windows")
[*]General partition info (as a guide, you can change these values to suite your hdd): / (root) 10GB, swap 2GB, /home remainder (that isn't already used by Windows or Linux partitions)
[/LIST]
Let us know if you have any questions or anything during install or afterwords!

---

### Post by RememberWhenItRained on 2011-04-06
okay, well i don't have an external drive (should probably think about getting one) so here goes:
is "ext4" also a linux partition?  so i need to delete extended, ext4, and linux swap? leave fat16, ntfs, and ntfs right?
(attached screenshot)

thank you seawolf, your help is much appreciated!

also the partitions appear to be unlocked, how do i unlock them to delete them with GParted?

---

### Post by seawolf167 on 2011-04-06
The reason to delete the partitions is to make it easier to make your partition table with Windows already installed - the install process also gives you the option to make a new partition table (I just figured this would be a little bit easier for someone new to the process since you have multiple Linux partitions and a Windows partition). So if you can't get this working you can simply start the install process and specify your partition table manually.

In order to "unlock" the partition, it is simply a matter of unmounting it, then you can make partition changes (try right clicking and selecting unmount).

You should NOT delete any NTFS, FAT, FAT32 partitions (those are your Windows partitions). You can see a printout of the partitions and their filetypes by entering this command in a terminal (Applications -> Accessories -> Terminal)

```
sudo fdisk -l
```

---

### Post by mastablasta on 2011-04-06
> **seawolf167 said:**
>  
For an intro book, there are tons of resources, the easiest to point to atm is the [Ubuntu Pocket Guide]("http://ubuntupocketguide.com/index_main.html") (it was written for an older version, but the basics are all still the same - when you get to more involved things there will be changes [example: GRUB -> GRUB2])
 
 
I think the easiest one is Ubuntu manual which is made for 10.04 he is trying to install.
 
LTS desktop are supported for 3 years, Server LTS 5.
 
Ext4 is a file system that linux uses on hard disk (Windows these days uses mostly NTFS)

---

### Post by RememberWhenItRained on 2011-04-06
> **seawolf167 said:**
> The reason to delete the partitions is to make it easier to make your partition table with Windows already installed - the install process also gives you the option to make a new partition table (I just figured this would be a little bit easier for someone new to the process since you have multiple Linux partitions and a Windows partition). So if you can't get this working you can simply start the install process and specify your partition table manually.

In order to "unlock" the partition, it is simply a matter of unmounting it, then you can make partition changes (try right clicking and selecting unmount).

You should NOT delete any NTFS, FAT, FAT32 partitions (those are your Windows partitions). You can see a printout of the partitions and their filetypes by entering this command in a terminal (Applications -> Accessories -> Terminal)

```
sudo fdisk -l
```

gosh i am such a noob - unmount is greyed out.

---

### Post by seawolf167 on 2011-04-06
You won't be able to unmount a LiveCD "partition" so just skip that one (plus you'll be able to see the partition table during the install process)

---

### Post by RememberWhenItRained on 2011-04-06
> **seawolf167 said:**
> You won't be able to unmount a LiveCD "partition" so just skip that one (plus you'll be able to see the partition table during the install process)

"that one" seems to be all of the partitions that appear to be linux. what am i doing wrong?:confused:

---

### Post by seawolf167 on 2011-04-06
No worries - just let the installer take care of it. Boot off the livecd, start the install, then simply delete & specify you partitions during the install process.

---

### Post by RememberWhenItRained on 2011-04-06
yeah, okay, that's what i was thinking; only thing is last time i tried that, i wasn't sure which partitions to delete. I'll give it another try though. Thanks again for all your help and patience.

---

### Post by seawolf167 on 2011-04-06
Since you are dual booting, you'll want to delete all but the Windows partitions (windows uses NTFS for the base OS and sometimes FAT/32 for recovery partitions). If you follow the manual partitioning scheme in the link I posted earlier you should be good to go.

---

### Post by RememberWhenItRained on 2011-04-06
> **seawolf167 said:**
> Since you are dual booting, you'll want to delete all but the Windows partitions (windows uses NTFS for the base OS and sometimes FAT/32 for recovery partitions). If you follow the manual partitioning scheme in the link I posted earlier you should be good to go.

so i booted off USB and began to install and selected manually partition. I set aside about 4GB for swap area (about the amount of RAM i have) and was going to set 10-15 GB (the more the merrier or not? i have a 500GB HD) for /root. I found the swap area in the drop down no problem, but what is root considered? I assumed/tried ext4 since that's what i saw earlier, but do i specify something else? /boot, etc. forgot what that dropdown was called? when i tried to proceed from ext4 it tells me that "no /root was defined" and to fix this problem in the manual partition table" or something to that effect.

also, is the SWAP or /root sizes i was going to use to big or too small?

---

### Post by RememberWhenItRained on 2011-04-06
Well Lucid Lynx is now up and running; thanks you two! 
A few quick questions for next time though: Did i need to create a /home partition, or would it have already been created for me?
Basic specs on my laptop is this: Dell Inspiron 14r with 500 GB HD, 4GB DDR2 RAM, etc. i read that /swap should be about double your RAM? so i partitioned 8GB for /swap, 20GB for /root, and 75GB for /home. given my specs, will these sizes work well?

thanks a lot!

(now to install my drivers...)

---

### Post by seawolf167 on 2011-04-06
When setting up the partition table if you didn't specify a separate /home partition it will be inside the / (root) partition.

An example partition setup (you can make however many you want - i.e. if you want to include /boot, /proc, etc.)

```
mount point        type       size
/                  ext4       10GB
swap               swap       2GB
/home              ext4       remainder of freespace
```Swap used to be 2x the amount of RAM your computer had (back in the day), now, since computers have so much RAM standard, you usually don't need to go over 2GB (even then with any modern computer you probably won't even access swap)

EDIT: forgot hardware drivers - go to System -> Administration -> Hardware Drivers for your available drivers (you'll need to be connected to the internet)

---

### Post by RememberWhenItRained on 2011-04-06
installed the drivers, still need to figure out my wireless info though. thanks for your help

---

### Post by RememberWhenItRained on 2011-04-06
nevermind, issue solved. seawolf, would you recommend my resizing the partitions or leave it be?

---

### Post by seawolf167 on 2011-04-06
Open up a terminal and type

```
sudo fdisk -l
```

then paste in here in between code tags so I can see your partition table and give an opinion :P

---

### Post by RememberWhenItRained on 2011-04-06
> **seawolf167 said:**
> Open up a terminal and type

```
sudo fdisk -l
```then paste in here in between code tags so I can see your partition table and give an opinion :P
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8d4a3023

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       35047   266108900    7  HPFS/NTFS
/dev/sda4           35047       47923   103425025    5  Extended
/dev/sda5           35047       36096     8425472   82  Linux swap / Solaris
/dev/sda6           36096       38586    19998720   83  Linux
/dev/sda7           38586       47923    74998784   83  Linux

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919841    b  W95 FAT32
```

---

### Post by seawolf167 on 2011-04-07
Sorry I'm going to have you run one more command I forgot earlier and post the output here:

```
mount
```

---

### Post by RememberWhenItRained on 2011-04-07
> **RememberWhenItRained said:**
> ```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8d4a3023

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       35047   266108900    7  HPFS/NTFS
/dev/sda4           35047       47923   103425025    5  Extended
/dev/sda5           35047       36096     8425472   82  Linux swap / Solaris
/dev/sda6           36096       38586    19998720   83  Linux
/dev/sda7           38586       47923    74998784   83  Linux

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919841    b  W95 FAT32
```
and
```
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda7 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/collin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=collin)
```

---

### Post by seawolf167 on 2011-04-07
> **RememberWhenItRained said:**
> 
[B]/dev/sda6 on / type ext4 (rw,errors=remount-ro)
/dev/sda7 on /home type ext4 (rw)[/B]

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       35047   266108900    7  HPFS/NTFS
/dev/sda4           35047       47923   103425025    5  Extended
[B]/dev/sda5           35047       36096     8425472   82  Linux swap / Solaris
/dev/sda6           36096       38586    19998720   83  Linux
/dev/sda7           38586       47923    74998784   83  Linux[/B]


Looks good

[LIST]
[*]sda5 is your swap (it could be a little smaller, but thats a moot point until you run out of hdd space :P)
[*]sda6 is your / partition, size looks ok
[*]sda7 is your /home partition (separate from /), size looks ok
[/LIST]
If you ever run out of Ubuntu /home space, you [probably] can easily steal some free space from your Windows partitions (simply resize Windows from within Windows, then fire up GParted and resize your home partition). Though chances are unless you rip a bunch of movies you probably won't run out of /home space.

---

