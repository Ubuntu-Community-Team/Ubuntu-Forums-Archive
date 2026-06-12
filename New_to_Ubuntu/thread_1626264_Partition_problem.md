---
title: "Partition problem"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by Myrmidon83 on 2010-11-20
I finally gave up on linux with my current 82845g gfx card, so I deleted it as I have done many times before and restored my master boot record, no problems.  However, when I look at my partitions in windows, I have my windows partion labelled as C: NTFS etc but I have another unlisted partition with no drive letter at a value larger than my hard drive. When I click to remove it, it says it is the active partition and all data will be lost.

If I boot with parted magic, it only sees this active partition which is 'unallocated'.

I'd really like my free space back.

Can anyone help me?

When I right click on the NTFS C: drive, it tells me it is disk 0, however the mystery drive just has the option to delete logical drive.  But it's making it out like it will wipe the whole disk if I delete it. :/

---

### Post by wishyjr on 2010-11-20
Hi,

in windows you can manage disks using something called the management console, you can access this by going to:

control panel > administrative tools > computer management

from here there is a disk management tool. open this.

From here you can view the physical disks on your machine. it should show a drive that has been unallocated. You should be able to either assign it a drive letter (d:,e: or whatever drive letter you wish as long as it isn't already used.)

i think you can also format the drive partition from there too. I assume that your linux installation was on that partition, you should be able to format it and use it again in windows.

hope that helps

Cheers
wishy

---

### Post by coffeecat on 2010-11-20
> **Myrmidon83 said:**
> I have another unlisted partition with no drive letter at [COLOR=Red]a value larger than my hard drive.[/COLOR]

.....


If I boot with parted magic, it only sees this active partition which is 'unallocated'.


Most likely, you have a false entry in the partition table with one partition listed as having its last sector beyond the physical end of the drive. If you mean that parted magic, which uses Gparted, is showing the whole drive as unallocated rather than the 'active' partition, then this is a known bug. See here for more:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

The fix is in that link, but it involves using a Linux live CD and editing the partition table with the use of sfdisk. If you are comfortable doing that, then that would probably be the best way to go. Do not try to use any software that uses parted as a backend, such as Parted magic, or Gparted from the live CD. It is parted that has the problem here and if you try to do anything with your partitions in this situation, you will likely destroy your Windows installation.

I really don't know whether any 3rd party Windows partitioning software would be the answer here. Acronis can cope with and create Linux filesystems but it too might get confused by the partition table problem - I don't know.

One answer might be to image the Windows C: drive with Norton Ghost, Acronis or Macrium Reflect, reformat the drive and then restore your Windows C:.

---

### Post by Myrmidon83 on 2010-11-20
Actually the solution was a lot simpler.  I just went into the disk management in windows, double checked the C: was the primary partition and deleted the weird logical partition then used parted magic to re-allocate the free space.

All sorted. :D

Decided it's time to update my laptop anyway so I'm gonna buy the eclipse from the novatech.co.uk website.

It has a geforce 8200 and from my research it should work ok with ubuntu.

I'll still be dual-booting though. :P

---

### Post by coffeecat on 2010-11-20
> **Myrmidon83 said:**
> Actually the solution was a lot simpler.  I just went into the disk management in windows, double checked the C: was the primary partition and deleted the weird logical partition then used parted magic to re-allocate the free space.

I should imagine the "weird" logical partition was in an extended partition that spilled over the end of the HD as described in that link, but the faulty partition table entry didn't upset the Windows disk management utility and it was able to delete it. Good to know that Windows Disk Management is blissfully aloof from such trivia as faulty partition tables. :wink:

But glad you've fixed it.

> **Myrmidon83 said:**
> Decided it's time to update my laptop anyway so I'm gonna buy the eclipse from the novatech.co.uk website.

Good luck with that!

---

