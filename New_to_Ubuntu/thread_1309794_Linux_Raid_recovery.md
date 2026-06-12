---
title: "Linux Raid recovery"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by RichardCL on 2009-11-01
Dear Forum,

I've just recieved a NAS system from a client with a stack of quite important data. The assumption was that RAID0 was fairly good as a backup. All concerned are now clear that it isn't but that doesn't return the data.

The motherboard in the NAS is broken, which leaves me with the SATA drive plugged into my Ubuntu desktop (Karmic, Core2Quad, 1.5TB internal SATA HDD) with a SATA to USB2 converter.

Disk utility shows me 3 partitions on the drive /dev/sdf, these are swap and two raid partitions. I'm pretty sure that the data I need is on /dev/sdf2 in a directory called /mnt/md1

My system tells me the drive is not mounted and cannot be mounted, just when I click on the drive.

I'm afraid to experiment and loose the data but I expect I need something like

```
sudo mount /dev/sdf2 /mnt/disk
```

and then just copy across. What is worrying me is that the partition type is listed as Linux RAID in disk utility.

Any tips before I start?

---

### Post by RichardCL on 2009-11-01
OK, I've done it (I think). Just need now to see what happens when the file operations are complete.

First I created a directory

```
mkdir /home/richard/NASCopy
```

Then I tried to mount the drive

```
sudo mount /dev/sdf2 /home/richard/NASCopy
```

This doesn't work because the file system is crippled by the previous raid. The error message:
> 
mount: unknown filesystem type 'linux_raid_member'

What I needed to do was just explicity tell mount that the RAID system is based on Linux non-journaling fs

```
sudo mount -t ext2 /dev/sdf2 /home/richard/NASCopy
```

Then
```

chown -R richard NASCopy
```

and the files are mine to view in Nautilus!

---

### Post by johndrem on 2010-05-21
Raid Recovery is the tool which automatically detect the type of the original RAID array while still allowing for fully manual operation. Raid Recovery is no doubt a highly valuable tool for users of all types of RAID arrays, whether hardware, native, or software. i think that's true.

---

### Post by mstrswrd06 on 2010-05-28
> **RichardCL said:**
> OK, I've done it (I think). Just need now to see what happens when the file operations are complete.

First I created a directory

```
mkdir /home/richard/NASCopy
```

Then I tried to mount the drive

```
sudo mount /dev/sdf2 /home/richard/NASCopy
```

This doesn't work because the file system is crippled by the previous raid. The error message:


What I needed to do was just explicity tell mount that the RAID system is based on Linux non-journaling fs

```
sudo mount -t ext2 /dev/sdf2 /home/richard/NASCopy
```

Then
```

chown -R richard NASCopy
```

and the files are mine to view in Nautilus!
This solution worked great for me! Had a Western Digital MyBook World Edition that got fried after a few  power outages. The motherboard was hopeless so I dissected the hard disk out of it and hooked it into my Ubuntu box (10.04). Was clueless when I found 4 RAIDed partitions on it and couldn't mount it. Mounting the primary partition (/dev/sdb4 [The largest one]) as ext2 and reassigning permissions solved my problem! Now I can recover my data and build myself a proper Ubuntu-based NAS. Thanks!

---

