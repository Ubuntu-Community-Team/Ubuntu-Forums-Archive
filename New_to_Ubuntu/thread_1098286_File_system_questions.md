---
title: "File system questions"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Volt9000 on 2009-03-16
1) Ok so I understand that fstab is the "file system table" file, which lists the devices to automount on startup (please correct me if I'm wrong.)

2) In another thread I read about /etc/mtab, which when I did a dump, appeared to just be a list of devices that are currently mounted (basically the mount command outputs the contents of this file.) Is this correct?

3) Now back to fstab. Is there a reason UUIDs are used in this file? Can I not just specify the partition, /dev/sdb1 instead of that long-winded string of letters and numbers? I would think that specifying the partition vs the UUID would be preferable because if partitions move, the UUID doesn't need to be updated.

4) To automatically mount a parition on startup I presume I would have to add a line to the fstab file. Assuming the output from mount (for this drive) is:

```

/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

Something along the lines of:

```

/dev/sda1    /media/disk    fuseblk    defaults

```

Or would I have to replace "defaults" with "rw,nosuid,nodev,allow_other,blksize=4096"?

What about the other parameters? In the fstab file it lists "dump" and "pass". What do these parameters mean?

---

### Post by drs305 on 2009-03-16
UUIDs are used since they do not change. A device designation, especially on an external drive, could change if another device was recognized first. Thus it could be sdb on one boot and sdc on the next. 

I would recommend ntfs-config for adding ntfs devices to fstab. "fuseblk" is just the way the system designates an ntfs file system in the mount command results.
```

sudo apt-get update
sudo apt-get install ntfs-config

```

Run it via System Tools, NTFS Configuration Tool or with "gksudo ntfs-config"

When you run ntfs-config, all you will have to do is tell it if the device is internal or external and the mount point name. (If you enter "data", the mount point will be /media/data).

---

### Post by Volt9000 on 2009-03-16
> **drs305 said:**
> UUIDs are used since they do not change. A device designation, especially on an external drive, could change if another device was recognized first. Thus it could be sdb on one boot and sdc on the next. 

I would recommend ntfs-config for adding ntfs devices to fstab. "fuseblk" is just the way the system designates an ntfs file system in the mount command results.
```

sudo apt-get update
sudo apt-get install ntfs-config

```

Run it via System Tools, NTFS Configuration Tool or with "gksudo ntfs-config"

When you run ntfs-config, all you will have to do is tell it if the device is internal or external and the mount point name. (If you enter "data", the mount point will be /media/data).

Hm, I already have ntfs-config installed and I don't see any option for typing in anything. This is what I see:

---

### Post by drs305 on 2009-03-16
Assuming it's an external device, tick the "enable write support" box, then OK, and the other options will become available.

ADDED: 

If it's easier for you to just edit fstab, this is what the entry would look like from ntfs-config:
```

/dev/sdXX /media/XXXX ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

Change sdXX to your device and XXXX to the mount point you must create if you aren't using ntfs-config. Note it doesn't use UUIDs. If you want, replace /dev/sdXX with UUID=XXXXXXXX with the XXXXXX being the UUID for the device (get it with "sudo blkid")

---

### Post by Volt9000 on 2009-03-16
Alright thanks.

What about my other questions?
And do I need to have the mount point already created, or does it get created automatically when the drive gets mounted?

---

### Post by drs305 on 2009-03-16
> **Volt9000 said:**
> Alright thanks.

What about my other questions?
And do I need to have the mount point already created, or does it get created automatically when the drive gets mounted?

ntfs-config will create it automatically. If you edit the fstab entry yourself you will have to create the mount point. For vfat/ntfs mounts, the ownership of the mount point isn't critical as it is established at the time of mounting by whoever mounts the device (user, root, etc). In general, as a sole user of a computer, I find it useful to make myself the owner of my mount points. Make the mount point, then set the ownership with:
```

sudo mkdir /media/mymountpoint  # create a mountpoint (conventionally /media for removable, /mnt for non-removable drives)
sudo chown -R yourusername: /media/mountpoint   # change the ownership to yourself
chmod -R 755 /media/mountpoint  # set permissions - 755 is a generic example


```

---

### Post by sarang on 2009-03-16
> **Volt9000 said:**
> 1) Ok so I understand that fstab is the "file system table" file, which lists the devices to automount on startup (please correct me if I'm wrong.)

It is indeed the file-system table, but not everything is automounted at startup. It is more like a table of known volumes and the default configurations for each of them. 
 

> **Volt9000 said:**
> 
2) In another thread I read about /etc/mtab, which when I did a dump, appeared to just be a list of devices that are currently mounted (basically the mount command outputs the contents of this file.) Is this correct? 

I think so.

> **Volt9000 said:**
> 
3) Now back to fstab. Is there a reason UUIDs are used in this file? Can I not just specify the partition, /dev/sdb1 instead of that long-winded string of letters and numbers? I would think that specifying the partition vs the UUID would be preferable because if partitions move, the UUID doesn't need to be updated.


Technically you could, but for smooth distribution-upgrades (intrepid to jaunty etc) I think keeping the UUID's is recommended. Also, the UUID's are a superior way of doing things IMO because then even if you change the physical order of disks on your machine or do things like raid, the disks will still be mounted at the original place - a Good Thing.

> **Volt9000 said:**
> 
4) To automatically mount a parition on startup I presume I would have to add a line to the fstab file. Assuming the output from mount (for this drive) is:

```

/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

Something along the lines of:

```

/dev/sda1    /media/disk    fuseblk    defaults

```

Or would I have to replace "defaults" with "rw,nosuid,nodev,allow_other,blksize=4096"?

What about the other parameters? In the fstab file it lists "dump" and "pass". What do these parameters mean?

[/quote]
Are you trying to mount a ntfs drive? In that case, the line you could add is: 
```
/dev/sda1	/media/sda1	ntfs-3g	defaults,users	0	0
```

If [FONT="Courier New"]ntfs-3g[/FONT] doesn't work, try replacing it with [FONT="Courier New"]ntfs[/FONT].

The fifth column, dump frequency, is used by some backup programs that do a block level dump. I usually set it to zero.

The sixth column decides fsck disk checking order. 'Scandisk' on windows is like fsck on *nix. Usually, set it to 1 for the / volume, 2 for ext3 volumes and 0 for ntfs volume. (0 = do not check, 1 = check first, 2 = check later).

The fourth column has comma separated mount options. Make sure you do not add any spaces between options. 
The order [FONT="Courier New"]defaults,users[/FONT] is important as options are applied in the order that they are specified. I think [FONT="Courier New"]users[/FONT] specifies that non-privileged users can mount that volume and also unmount it, irrespective of who mounted it. This is not the default behavior, but the option [FONT="Courier New"]users[/FONT] chooses this. Reversing the order to [FONT="Courier New"]users,defaults[/FONT] would not work as the [FONT="Courier New"]defaults[/FONT] option would override the [FONT="Courier New"]users[/FONT] option.

For more info, run 
```
man fstab
```
to bring up the fstab _man_ual page. Often, [FONT="Courier New"]man foo[/FONT] will give useful information about [FONT="Courier New"]foo[/FONT].

Also see [http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab) - it is an article I have often found to be useful.

---

### Post by Volt9000 on 2009-03-16
Great, thanks for your help, everyone!

---

