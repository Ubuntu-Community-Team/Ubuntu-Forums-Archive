---
title: "Monitor Out Of Range"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by DirtyPC on 2010-10-26
hello all, I was recently playing Frets on Fire, but open browsing songs my pc froze, nothing would unfreeze it so i turned it off by the plug. now when I turn it on, my monitor says, out of range

any ideas? Remember im a novice on this stuff so dont be too complicated..

---

### Post by cariboo on 2010-10-26
Boot from the Live Cd and once at the desktop, open a terminal and type:

```
sudo fsck -y /dev/sdaX
```

where /dev/sdaX is the / partition of you Ubuntu install. If you aren't sure what the / partition is, type:

```
sudo fdisk -l
```

in the same terminal, the output should look similar to this:

```
sudo fdisk -l
[sudo] password for cariboo: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005653a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       10199    81817600    7  HPFS/NTFS
/dev/sda3           10199       19458    74368001    5  Extended
/dev/sda5           10199       11415     9764864   83  Linux
/dev/sda6           11415       19458    64602112   83  Linux
```

in the above example /dev/sda5 is my / partition.

---

### Post by DirtyPC on 2010-10-26
1st things first, I said please try and make it simple, and to me, that was Matrix code, + I don't have a live CD, as I downloaded via the wubi installer

Thanks anyway, turns out all I had to do was press Ctrl+Alt+-, then change the resolution back to 1280x1024. I havn't restarted it yet, but i'm hopeful:guitar:

---

### Post by srs5694 on 2010-10-26
Cariboo907,

This is unrelated to harrylucas1's problem, which I gather is now solved, but your disk seems to have remnants of a GUID Partition Table (GPT) configuration along with non-GPT Master Boot Record (MBR) partitions. This is potentially dangerous. Among other things, this problem *will* cause the Ubuntu installer to fail to find *any* partitions -- it'll look like the disk is completely unpartitioned. See [this recent thread](http://ubuntuforums.org/showthread.php?t=1604074) for an example, and particularly [my post](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34) for the fix. I recommend you take care of this problem. You might be able to live with it for an indeterminate period of time, but it's conceivable that you'll eventually try to run some utility or other that will damage your system when it sees that configuration. (I don't know of such a utility offhand, but I know how easy it would be to write one that wouldn't do the appropriate checks and that would therefore blindly do something very bad.)

---

### Post by DooM55 on 2010-10-26
> **harrylucas1 said:**
> hello all, I was recently playing Frets on Fire, but open browsing songs my pc froze, nothing would unfreeze it so i turned it off by the plug. now when I turn it on, my monitor says, out of range

any ideas? Remember im a novice on this stuff so dont be too complicated..


try

sudo apt-get update

---

### Post by DirtyPC on 2010-10-27
Bad news... I restarted it, and again.. out of range, so again I press CTRL+ALT+-, then i enter my login details, then it goes straight back to the correct resolution 1280x1024, the problem only seems to be at the login

@ Tried that, will see what happens, i'm guessing your trying to update my video drivers via the terminal?

---

