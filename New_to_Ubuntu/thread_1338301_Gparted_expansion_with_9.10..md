---
title: "Gparted expansion with 9.10."
date: 2009-11-26
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2009-11-26
I may need to expand the size of my partitions in 9.10. I usually use Gparted for this. However lately I've been doing the separate / and /home partitions.

Would there be any problems expanding just the /home folder?

---

### Post by ukripper on 2009-11-26
> **emeraldgirl08 said:**
> I may need to expand the size of my partitions in 9.10. I usually use Gparted for this. However lately I've been doing the separate / and /home partitions.

Would there be any problems expanding just the /home folder?

Depends. If you have space infront or at back of home partition then yes you can use gparted easily to extend your current home. otherwise it will be bit tricky and still achievable by wokring around. 

In that case I'd always create LVM volume first if i have to increase home partition at later stage. That way I don't have to worry about how much space i need to save.

---

### Post by emeraldgirl08 on 2009-11-26
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004506a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2612        3526     7349737+  83  Linux
/dev/sda3            3527        4574     8418060    5  Extended
/dev/sda4            4575        5880    10490445    7  HPFS/NTFS
/dev/sda5            3527        4441     7349706   83  Linux
/dev/sda6            4442        4574     1068291   82  Linux swap / Solaris
```

This is my setup. The sda4 NTFS part is a shared partition. I don't use it so I'm probably going to delete it anyway.

---

### Post by ukripper on 2009-11-26
can you post output of mount too:
```
sudo mount
```

---

### Post by emeraldgirl08 on 2009-11-26
```
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda5 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nurset/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nurset
```

---

### Post by ukripper on 2009-11-26
ok so your home is on /sda5 I think you shouldn't have any problem extending it using space allocated from /sda4. just make sure you repartition /sda4 to ext4 and then merge with home.

Make sure you have backup of your home and backup of important data from NTFS too.

---

### Post by kansasnoob on 2009-11-26
Please post the output of:

```
sudo parted /dev/sda print
```

and:

```
df -H
```

---

### Post by emeraldgirl08 on 2009-11-26
```
Model: ATA ST980815A (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  21.5GB  21.5GB  primary   ntfs            boot
 2      21.5GB  29.0GB  7526MB  primary   ext4
 3      29.0GB  37.6GB  8620MB  extended
 5      29.0GB  36.5GB  7526MB  logical   ext4
 6      36.5GB  37.6GB  1094MB  logical   linux-swap(v1)
 4      37.6GB  48.4GB  10.7GB  primary   ntfs

```

and...

```
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda2              7.5G   4.3G   2.9G  60% /
udev                   724M   295k   724M   1% /dev
none                   724M   1.3M   723M   1% /dev/shm
none                   724M    87k   724M   1% /var/run
none                   724M      0   724M   0% /var/lock
none                   724M      0   724M   0% /lib/init/rw
/dev/sda5              7.5G   1.2G   5.9G  17% /home

```

---

### Post by kansasnoob on 2009-11-26
> **emeraldgirl08 said:**
> ```
Model: ATA ST980815A (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  21.5GB  21.5GB  primary   ntfs            boot
 2      21.5GB  29.0GB  7526MB  primary   ext4
 3      29.0GB  37.6GB  8620MB  extended
 5      29.0GB  36.5GB  7526MB  logical   ext4
 6      36.5GB  37.6GB  1094MB  logical   linux-swap(v1)
 4      37.6GB  48.4GB  10.7GB  primary   ntfs

```

and...

```
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda2              7.5G   4.3G   2.9G  60% /
udev                   724M   295k   724M   1% /dev
none                   724M   1.3M   723M   1% /dev/shm
none                   724M    87k   724M   1% /var/run
none                   724M      0   724M   0% /var/lock
none                   724M      0   724M   0% /lib/init/rw
/dev/sda5              7.5G   1.2G   5.9G  17% /home

```

The reason I asked for "sudo parted /dev/sda print" is that it shows the partitions in their actual order whereas "fdisk -l" does not. So, we know that Jaunty / is on sda2 and /home is on sda5, and from this:

> Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  21.5GB  21.5GB  primary   ntfs            boot
 2      21.5GB  29.0GB  7526MB  primary   ext4
 3      29.0GB  37.6GB  8620MB  extended
 5      29.0GB  36.5GB  7526MB  logical   ext4
 6      36.5GB  37.6GB  1094MB  logical   linux-swap(v1)
 4      37.6GB  48.4GB  10.7GB  primary   ntfs

We know that your swap (sda6) is actually in between your /home (sda5) and the ntfs storage you want to delete (sda4).

**[COLOR="Red"]Note: I'm assuming that you have no data on sda4 that needs to be saved![/COLOR]**

So it looks like if you want to delete sda4 and add that space to sda5 you would first have to delete sda4, then move swap all the way to the right, then resize sda5 to use the free space.

There's only one hangup to that. When swap is moved or resized it messes up some uuid's, which causes you to lose the quiet splash and also swap will not be "on" after each reboot. I wrote about that here (skip down to where I added the red **[COLOR="Red"]*[/COLOR]**'s:

[http://ubuntuforums.org/showpost.php?p=8359445&postcount=16](http://ubuntuforums.org/showpost.php?p=8359445&postcount=16)

Sadly, if you read all post's in that thread, we couldn't get the quiet splash back and I couldn't figure out why! I'm still puzzled over that because I've used that technique dozens of times without trouble.

Still, a failure is just that: a failure. So if my method failed once it could fail again!

I actually learned that from coffeecat and I notice he's been active here recently. I keep bumping that hoping he (or someone) will see what I might have missed.

Anyway it's up to you if you wish to proceed. Based on the fact that I've used that method dozens of times successfully and had one failure on a box that wasn't right in front of me says, "yes, go ahead", but I want you to know my method failed at least once!

---

### Post by emeraldgirl08 on 2009-11-26
I am hesitant now.

Things are running nicely now so I don't want to hose my system. A reinstall seems to be the answer but an afternoon of updates isn't appealing. I think I'll hold off on this for the time being. 

One other thing. For future installations would it be better to have swap between / and /home???

---

### Post by egalvan on 2009-11-26
kansasnoob, remember that swap is a logical, so the containing extended needs to be resized first.
(query: can an extended be re-sized whilst still containing logicals?)

Also, this need to be done from a LiveCD (PatedMagic is excellent).

And lastly, have you had a chance to test my theory of "re-naming" swap's UUID back to it's original value?

(save swap's UUID with "sudo blkid", change swap, reset swap's UUID to the original value)

No changes needed to grub, fstab or initramfs...

My "play" machine is down for the count ( messed it up royally playing with an up-grade :) ) so I can't test this myself right now.

---

### Post by egalvan on 2009-11-26
> **emeraldgirl08 said:**
> 
One other thing. For future installations would it be better to have swap between / and /home???

It doesn't really matter.

On *my* installs, I always have swap as a buffer between the Windows partition (which is *always* first, 'cause MS does not play nice with others) ,
 another buffer , and an extended partition.

thus...
primary -- Windows, usually 10GB
primary -- swap , usually 2GB
primary -- filler, usually 2GB
extended -- linux logicals, as many as I need. this takes all available space, and may at times contain an NTFS partition for exchange between Linux and Windows.


Just about everybody has his own ideas/opinions.

Min is just that,,,
my idea of an opinion :)

---

### Post by kansasnoob on 2009-11-26
> **emeraldgirl08 said:**
> I am hesitant now.

Things are running nicely now so I don't want to hose my system. A reinstall seems to be the answer but an afternoon of updates isn't appealing. I think I'll hold off on this for the time being. 

One other thing. For future installations would it be better to have swap between / and /home???

Well, your /home is only 17% used so you have nearly 6gb to play with while pondering this.

Egalvan pointed out something that I hadn't mentioned: since that ntfs data partition (sda4) is a primary partition, after deleting it you would first have to expand the extended partition (sda3) all the way to the right, then move swap, and then expand your /home.

As far as where swap should be, at one end or the other of the extended partition would be preferable. But who am I to talk:

[ATTACH]137690[/ATTACH]

I cloned that from a smaller drive that was getting so loud it scared the dogs and I left swap just where it landed:)

---

### Post by emeraldgirl08 on 2009-11-26
Well I tried installing it on the W7 side of the boot and it installed...but it won't play. This is a sad state of affairs now. It took 3gb of filespace. I don't know how much bigger that would get after a couple of weeks of playing with.

I sort of had a feeling it would not work b/c Wolfenstein Enemy Territory won't play on my W7 either. So..

I'm thinking that I should try and install it on Linux. I'm on and off here on the forum right now b/c of Turkey Dinner preparations so I'll be back later to read up some more.

Thanks guys :)

---

### Post by kansasnoob on 2009-11-26
> **emeraldgirl08 said:**
> Well I tried installing it on the W7 side of the boot and it installed...but it won't play. This is a sad state of affairs now. It took 3gb of filespace. I don't know how much bigger that would get after a couple of weeks of playing with.

I sort of had a feeling it would not work b/c Wolfenstein Enemy Territory won't play on my W7 either. So..

I'm thinking that I should try and install it on Linux. I'm on and off here on the forum right now b/c of Turkey Dinner preparations so I'll be back later to read up some more.

Thanks guys :)

OMG! Tell me you didn't resize Win 7 with gparted!

That could be very, very bad!

Certainly nothing even near what we discussed here!

---

### Post by emeraldgirl08 on 2009-11-26
:D

lol. No I did not resize Windows 7. I was curious so I installed the game into my empty NTFS partition. So... getting this game to work for my situation seems to be to install it into /home. 

Since it doesn't want to work with my W7 I'll just uninstall it and try it with linux. 

Seems like my evening has been planned now.

---

