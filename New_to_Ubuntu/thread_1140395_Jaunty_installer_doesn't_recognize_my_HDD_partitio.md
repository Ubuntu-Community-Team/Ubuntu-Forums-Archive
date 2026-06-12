---
title: "Jaunty installer doesn't recognize my HDD partitions"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by doctorbighands on 2009-04-27
I just went to do a fresh install of 9.04. When it gets to the partitioner, it lists my entire hard drive as "unallocated space." This is odd, because I have Vista installed along with a sizeable, separate media partition, as well as Ubuntu (three partitions total, along with swap).

Anyone know why this is happening and what I do to get around it? I don't want to have to reinstall Vista nor the content in my media partition just to get Jaunty installed.

Thank you!

EDIT: Also, I checked again using Gparted in the Live CD, and it doesn't recognize anything on my hard disk either. What gives?

---

### Post by doctorbighands on 2009-04-27
...bump?

---

### Post by JoshuaRL on 2009-04-27
Are you still able to boot into Vista without problems?  If so, could you please boot into the LiveCD again.  Then go to Applications->Accessories->Terminal and copy this in:
```
sudo fdisk -l
```
That will list all the partitions on any disks connected to the computer.  Take the output and post it back here wrapped in [noparse]```
 tags 
```[/noparse] and we'll see what it says.

---

### Post by doctorbighands on 2009-04-27
Yep, I can boot into Vista just fine.

I restarted the live CD, and Gparted still lists my drive as unallocated.

"sudo fdisk -l" returns the following:
```

omitting empty partition (5)

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009255a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1570    12610993+  83  Linux
/dev/sda2   *        1571        4366    22458870    7  HPFS/NTFS
/dev/sda3            4367       12161    62613337+   5  Extended
/dev/sda4           11662       12161     4016218+  82  Linux swap / Solaris
/dev/sda5            4367       11661    58597024+   b  W95 FAT32

```

---

### Post by doctorbighands on 2009-04-27
...bump again?

---

### Post by doctorbighands on 2009-04-27
Have I found an unsolvable problem? I hope not...

---

### Post by JoshuaRL on 2009-04-27
That's strange.  You have an ext3 partition that fdisk sees, but for some reason GPartEd doesn't.  I hate to ask this of you, but could you acquire and burn a Parted Magic ISO?  Here's the site:

[http://partedmagic.com/](http://partedmagic.com/)

See if it can see your hard drive correctly.

---

### Post by doctorbighands on 2009-04-27
PartedMagic is telling me the same thing as the Jaunty disc: unallocated space.

This is really weird.

---

### Post by aknight_sa on 2009-04-28
GParted nor the installation partitioner can see my hard disk.. help needed!!

it just reads.. and nothing happens

---

### Post by doctorbighands on 2009-04-28
I'm still having problems myself.

I just booted into Ubuntu (the version installed on my HDD), opened Gparted, and it tells me that the disk is unallocated.

It's a puzzle: Why can fdisk see my partitions, but not Gparted?

---

### Post by longtom on 2009-04-28
> **doctorbighands said:**
> I'm still having problems myself.

I just booted into Ubuntu (the version installed on my HDD), opened Gparted, and it tells me that the disk is unallocated.

It's a puzzle: Why can fdisk see my partitions, but not Gparted?

Look, I don't want to make fun of you and I am a beginner myself but....

did you choose the correct hd you want to work with in gparted?  If I remember correctly, I had to choose from a little drop down window to the top right.

For what it is worth...

---

### Post by wizard10000 on 2009-04-28
I'm guessing here so please take what I say with a grain of salt  :)

Vista partitions disks differently than XP and earlier do - the Vista partitioner will split a disk on a 1mb boundary where every other partitioner on the planet uses cylinder boundaries to partition disks.  You need a fairly current version of gparted to manage a partition created by Vista.  Don't know whether the version of gparted on the Jaunty CD is new enough but expect it might be.

Another idea - are you using bitlocker on the Vista partition?  I'm wondering if the partition is encrypted.

---

### Post by doctorbighands on 2009-04-28
> **wizard10000 said:**
> I'm guessing here so please take what I say with a grain of salt  :)

Vista partitions disks differently than XP and earlier do - the Vista partitioner will split a disk on a 1mb boundary where every other partitioner on the planet uses cylinder boundaries to partition disks.  You need a fairly current version of gparted to manage a partition created by Vista.  Don't know whether the version of gparted on the Jaunty CD is new enough but expect it might be.

Another idea - are you using bitlocker on the Vista partition?  I'm wondering if the partition is encrypted.

I'm not sure if I used Vista to partition the disk originally, but I very well may have. If that's the case, should I expect to have to wipe the disk clean before a proper installation?

If I'm using bitlocker, it isn't intentional (I've never heard of such a thing). I'll do my best to check and see, but if the partition is encrypted, that sounds like a viable solution.

Thank you!

---

### Post by doctorbighands on 2009-04-28
> **longtom said:**
> Look, I don't want to make fun of you and I am a beginner myself but....

did you choose the correct hd you want to work with in gparted?  If I remember correctly, I had to choose from a little drop down window to the top right.

For what it is worth...

I have only one disk from which to choose, so yes, the proper one was selected.

---

### Post by doctorbighands on 2009-04-28
It turns out I'm not using BitLocker. It isn't available on the version of Vista that I'm using (Business).

Also, I'm reasonably certain that I didn't use Vista to partition the drive. If anything, it was XP, as that's what I originally installed on this machine.

---

### Post by wwusnobrdr on 2009-04-28
Make sure you have ntfs-3g installed and possible ntfs-progs.  This should be installed on the livecd, but I am perplexed as well.

---

### Post by doctorbighands on 2009-04-28
I just double-checked, and ntfs-3g and ntfs-progs are both installed.

*sigh*

---

### Post by doctorbighands on 2009-04-28
Should I submit a bug report for this?

---

### Post by R@inm@n on 2009-04-28
Whilst my problem wasn't the same as yours exactly, it was similar.

I installed 9.04 onto a second HDD in my computer, the other HDD contains Win XP.

Now, after installation of Jaunty Jackalope, Grub can't see my Win XP HDD and I can't boot into it because Grub doesn't give me that option like Hardy used to.  I believe that it is a 'bug' in Jaunty and is quite a common one from what I have been reading.


 R.

---

### Post by egalvan on 2009-04-28
> **doctorbighands said:**
> 

"sudo fdisk -l" returns the following:
```

[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009255a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1570    12610993+  83  Linux
/dev/sda2   *        1571        4366    22458870    7  HPFS/NTFS
[COLOR="Red"]/dev/sda3            4367       12161  [/COLOR]  62613337+   5  Extended
[COLOR="Red"]/dev/sda4           11662       12161 [/color]    4016218+  82  Linux swap / Solaris
/dev/sda5            4367       11661   58597024+   b   W95 FAT32
``` 

Definite problems...
[COLOR="Red"]
sda4[/COLOR] should be a primary partition,
but it is inside the extended partition [COLOR="Red"]sda3[/COLOR]

extended partition numbering starts with "5"
sda5

even curiouser, this post is very similar...

[http://ubuntuforums.org/showthread.php?t=1057360](http://ubuntuforums.org/showthread.php?t=1057360)

And your second partition is defined as the boot partition...
windows does not like being anything other than number one...
you CAN make it work, but it's work...

I'm not good enough to help any further...
other gurus will have to chime in... :)

ErnestG

---

### Post by longtom on 2009-04-30
> **egalvan said:**
> Definite problems...

windows does not like being anything other than number one...
you CAN make it work, but it's work...

ErnestG

My Windows XP Partition is sdb2, with sda1 (swap) sda2 (8.10) and sdb1 (storage) being ahaead in the "pecking order".  Ther is still a sdb3 and sdb4 behind it as well.

My Windows doesn't need to be Number 1....

but I probably understood you wrong...

---

### Post by egalvan on 2009-05-01
> **longtom said:**
> ...
My Windows doesn't **need **to be Number 1....

but **I probably understood you wrong**...

Yep, since I said that Windows **likes** to be Number 1... :)

On a regular Windows Install...

Windows installd itself on the **first physical partitio**n of the **first physical drive**,
and then call that **Drive C** :)

If this is not possible, Windows tends to complain.

Yes, it **is** possible to do so, using any number of tricks, work-arounds and jumping through hoops, etc...
I've done this any number of times, for reasons galore.

But it is NOT as simple as installing Linux anywhere one desires.

And it is a pitfall that un-wary computer users can fall into, 
and then need help getting out of.

And the sdax / sdbx etc system of naming/numbering is *nix-oriented.
And the partitions can be numbered differently than their actual order on the drive...
In fact, partition-type programs (such as gparted) will advise

"partitions not in disk order"

if they are "out-of-order"

And I said "advise", not complain :)

GRUB and other *nix'y type software does not seem to care about it.

:guitar:

---

### Post by doctorbighands on 2009-05-04
I still haven't found a solution to this problem, other than wiping the drive clean and completely reinstalling everything (which, I hope you can understand, I am VERY reluctant to do). If there's any possible way to get Gparted to see my partitions, I'd really love to know about it!

---

