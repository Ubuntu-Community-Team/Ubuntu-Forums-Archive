---
title: "struggling with cloning to replace my Ubuntu hard drive"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by mystmaiden on 2011-02-08
I have Ubuntu 10.04 LTS on a drive that's going bad but its exactly like I want it so I'd like to clone it over to a second drive in as simple a fashion as possible. I have the second drive repartitioned and ready but I'm struggling a bit understanding clonezilla.  Since I'll be pulling the old drive as soon as the process is complete would I choose disk to disk rather than an image? The Clonezilla site says choose an image, but it Seems like that would be for backup.

I've labeled the second drive 'clone' for now, ext4. It's 80 gb and the drive I'm cloning is 60gb

First of all is cloning the disk the best way to go about this - or would another method be better/safer? 

Also, in my fumbling I wound up with an extra partition on my places list that no longer exists but Ubuntu seems to think it does. How do I remove it? (My first attempt at reformatting the new drive I'd added a data partition and then realized that made the drive space too small for the clone so I deleted it using a live Ubuntu cd and g-parted.)



thanks in advance,

mystmaiden

---

### Post by Paqman on 2011-02-08
A disk-to-disk copy is exactly what it sounds like, you don't need to prep the destination at all, it just copies everything over to the new disk. Just go ahead and clone disk-to-disk, you don't need to mess about doing each partition.

---

### Post by Rhizoid on 2011-02-08
Depending on how bad the older drive is you might find you have more luck with ddrescue than either clonezilla or dd

[http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

However, if you don't currently suffer any read errors on the old drive then booting from a livecd or usb and issuing this in terminal (where *x* is the letter of the old drive and *y* is the new one) Please see the [COLOR=Red]WARNING[/COLOR] below before starting:

```
dd if=/dev/sd*x* of=/dev/sd*y* bs=1024k conv=noerrors
```Will directly copy your entire system from disk to disk.

[COLOR=red]WARNING[/COLOR]

Getting mixed up between *x* and *y* will overwrite your system with the contents of a completely empty disk - it's a great way to wipe a system very quickly as the first bits which get overwritten are track0 and the partition information.  Please be absolutely sure which is *x *and which is* y* before you start.  If in doubt ask for more help.

Cheers,

---

### Post by mystmaiden on 2011-02-08
Thank you for the replies, I can't tell you how grateful I am.

I'd like to avoid clonezilla if possible, it makes me a bit nervous because I don't understand it completely, and I've seen quite a few error reports in my searching around. Probably a perfectly fine program but if others are having issues - I feel I will too.

Rhizoid wrote -

> However, if you don't currently suffer any read errors on the old drive then booting from a livecd or usb and issuing this in terminal (where x is the letter of the old drive and y is the new one) Please see the WARNING below before starting:

Code:

dd if=/dev/sdx of=/dev/sdy bs=1024k conv=noerrors

Will directly copy your entire system from disk to disk.
I can boot and use the original hard drive just fine but the disk was clicking and beeping from time to time and shows bad sectors on disk utility so its time for it to go before it crashes. I did try and fix it with a few methods after backing things up but its still showing problems on the disk utility screen. (Warning 6 bad sectors, normalized 251, worst 251, threshold 63, value 6 bad sectors)

In what state should the new drive be in when I start this. Right now its installed and partitioned with one ext4 and labeled 'clone' 

Currently - 
```
 

Disk /dev/sda: 61.5 GB, 61475807232 bytes
255 heads, 63 sectors/track, 7474 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7189    57744618+  83  Linux
/dev/sda2            7219        7474     2055169    5  Extended
/dev/sda5            7219        7474     2055168   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004a7f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

```Now to make sure I'm understanding this, the correct command would be

```
dd if=/dev/sda of=/dev/sdb bs=1024k conv=noerrors
```And it would copy every partition and all my data, etc and be bootable?

thank you again,

mystmaiden

---

### Post by Paqman on 2011-02-08
Using dd will copy every single thing on the drive, bit for bit. The downside of it is that it's not very smart, and will waste a lot of time copying the free space on the disk as well. Obviously that's less of a problem if you've got a really full disk, or aren't in a hurry. Your disk is fairly small though, so it shouldn't take too long.

---

### Post by Rhizoid on 2011-02-08
> **mystmaiden said:**
> Thank you for the replies, I can't tell you how grateful I am.
```
 

Disk /dev/sda: 61.5 GB, 61475807232 bytes
255 heads, 63 sectors/track, 7474 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7189    57744618+  83  Linux
/dev/sda2            7219        7474     2055169    5  Extended
/dev/sda5            7219        7474     2055168   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004a7f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

```Now to make sure I'm understanding this, the correct command would be

```
dd if=/dev/sda of=/dev/sdb bs=1024k conv=noerrors
```And it would copy every partition and all my data, etc and be bootable?

thank you again,

mystmaiden

Ok - you've got the code correct for the devices.  However, on re-reading and checking it should be;
```
 dd if=/dev/sda of=/dev/sdb bs=1024k conv=noerror
```

My bad - I typed noerrors and it should be singular not plural ;)

A small difference but it will stop it crapping out on you because it doesn't recognize the option.

Likewise, /dev is owned by root so the operation will fail unless you run it as a superuser, so;

```
sudo dd if=/dev/sda of=/dev/sdb bs=1024k conv=noerror
```

It will copy /dev/sda to /dev/sdb in it's entirety as noted by Paqman.  As that includes the partition information, the code in the MBR and the UUID it will indeed be bootable, provided you disable or better yet remove the old drive before restarting - if you don't there will probably be some conflict messages as the system won't be able to see the difference between the disks once Ubuntu starts.  As the new drive is a little larger than the old one you'll have some unused space left which you can either create a new partition in or increase the size of the existing partitions with.

If in any doubt, don't press the return key and ask a grown-up* to sanity check my code above.

*grown-up in this sense is someone who knows a bit about Linux, regardless of age or maturity ;)

Cheers,

---

### Post by mystmaiden on 2011-02-08
Success! The drive copied and booted perfectly and the old one has been pulled. I'll probably try the disk rescue that you mentioned, Rhizoid - now that everything is safely up and running.

thanks so much!!

mystmaiden

---

