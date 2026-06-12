---
title: "Problems with triple boot and mounting drive"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by poisencrazy on 2009-03-31
Originally I had a dual boot setup of Vista and Ubuntu on my laptop.
It turns out that my laptop has had several wifi issues when using Ubuntu (Compaq C700) and after trying every method to solve this, I resorted to going from a dual boot to a triple boot and including backtrack 3 (which had no wifi problems).

The problem with this was that when I installed backtrack 3, it installed lilo as its boot manager, which I couldn't configure correctly.
I tried every combination of ```
other = sdaX
``` and it still refused to show any of my operating systems besides Backtrack.

So after that, I decided to reinstall Grub (because I've had more experience with it in the past and felt more comfortable using it). Once I did this however, I noticed that the 'Find' 'setup' and 'root' commands would not work. Any command that I needed to setup Grub would not work, so I did some googling and found a tutorial on how to setup through a linux command line.
Lucky me, I still had my live CD of backtrack 3, so I decided to use that.
I did everything the tutorial said with success, rebooted, and still no results.
I switched back to Backtrack, and found that my SDA1 partition would not mount, and I still cant boot any of my Operating systems.

The sudo fdisk -l -u displays this:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   247567382   123783660    7  HPFS/NTFS
/dev/sda2       247567383   288527399    20480008+   5  Extended
/dev/sda3       288527400   312576704    12024652+   7  HPFS/NTFS
/dev/sda5       247567446   268060589    10246572   83  Linux
/dev/sda6       268060653   287563499     9751423+  83  Linux
/dev/sda7       287563563   288527399      481918+  82  Linux swap

```

I get this when i try to mount sda1
```
bt ~ # mount /dev/sda1
Unexpected clusters per mft record (0).
Tried to free NULL inode pointer (0x805332c)
Tried to free NULL attribute pointer (0x8053384)
Tried to free NULL inode pointer (0x8053380)
Tried to free NULL attribute pointer (0x8053398)
Tried to free NULL attribute pointer (0x8053394)
Tried to free NULL inode pointer (0x8053390)
Tried to free NULL attribute pointer (0x80533ac)
Tried to free NULL inode pointer (0x80533a8)
Failed to startup volume: Invalid argument
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

The strange thing is that when I do a ```
cfdisk /dev/sda
```
it displays the partitions with different numberings. o_O o_O o_O

So basically, I need to know how I can mount my drive >>

---

### Post by poisencrazy on 2009-03-31
bump


Ive done some googling and nothing helps
If i cfdisk and change the file system type would that possibly solve my problem?
That drive has my vista and all of my work/scrips that ive written =/
I'd hate to lose that.

---

### Post by poisencrazy on 2009-04-02
Meh. I had to reformat the vista partition. I managed to mess up the first few bytes of the drive when i was doing something which made it unreadable

---

