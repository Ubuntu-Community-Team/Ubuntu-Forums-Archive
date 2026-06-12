---
title: "multiboot help"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by nml on 2009-04-06
I know this is the type subject that is continually repeated, but I think I may be to dense to get it...

I currently have a single 80gig HD (laptop) that is successfully duel booted with Ubuntu 8.10 and XPro.....

From the 8.10 live CD, GParted says it's divided as follows:

/dev/sda1   ext3   61.7 g
unallocated
/dev/sda2   ntfs   9.7 g
unallocated
/dev/sda3   extended   3.08 g
     /dev/sda5   linux-swap

(png attached to message---I didn't know how to post this pic from GParted on the liveCD)

I want to add a third OS (another linux distro) and slightly enlarge my XP parition.....

I'm not really worried about crashing the installations or backing up the data as all can be reinstalled (but would rather not do so due to time and effort issues...)

What's the best way to do this......unfortunately I need fairly simple answers..

TIA

Mick

---

### Post by lamalex on 2009-04-06
Just resize /dev/sda1 down so theres enough unallocated space to expand your XP partition, and create a new one for the other os. Also, I don't know what your hardware specs are like but have you thought about using virtualization instead of partitioning again? Might be easier.

---

### Post by drs305 on 2009-04-06
If you are just looking for how to move/setup the partitions, this is one way. As you noted, make sure your important data is backed up.

1. Shrink sda1
2. Move & expand sda2 to the left, touching sda1, leaving the desired amount of free space to the right. This will take a while as you are moving a partition to the left and all the data has to be moved.
3. Expand sda3 (extended partition) to take up all remaining free space.
4. Create your new OS partition within sda3 (extended partition).

Do all this from the livecd, since you cannot have your OS mounted while you do this.

Check your version of gparted to check compatibility with NTFS partitions (View, File System Support). If the NTFS entries aren't enabled, install ntfsprogs and check again.
```

sudo apt-get install ntfsprogs

```

---

### Post by nml on 2009-04-06
Many thanks for the instructions....

so if I shrink sda1 down to about 40gigs, then expand the nfts (windows) partition to 20 gigs, then my sda3 should be large enough to mess with another linux distro....assuming I don't mess anything up, after installing my next distro, will I have to do anything to the grub boot loader (?menu.lst?) to make them all choices on boot?

> have you thought about using virtualization instead of partitioning again? Might be easier.

no, but I guess I should have....I may try that route instead if I chicken out with repartitioning what I have.....

thanks,

Mick

---

### Post by carml on 2009-04-06
BTW if I would be in you,I'd try to allocate those two gery unallocated spaces said that,to make your test for fun you can install e.g. Virtualbox and install there every OS you want.You'll need only some free space under Xp or Linux,no need to touch the partitions ;)

---

### Post by nml on 2009-04-06
Thinking over the replies.....I think the virtualiztion route may be the way to try new versions of linux.....

But,I still need more room for the XP OS.......

What are the chances of not running into an OS problem if I just shrink sda1, then enlarge sda2 (for more XP room)?

thanks for all the help....

Mick

---

### Post by drs305 on 2009-04-06
nml,

There are no guarantees. I've done it dozens of times without incident. Make sure of your power sources and cross your fingers.

Once you have done what you suggest, you might as well expand the extended partition as well. Having a large extended partition will give you a lot of flexibility for further partitions. Just make sure you leave enough for 1 and 2 because transferring space from an extended partition back to a primary is a pain.

I have a partition dedicated to VMs and it's great. You can install and test all sorts of things without making a bunch of different partitions.

---

### Post by nml on 2009-04-06
> I have a partition dedicated to VMs and it's great. You can install and test all sorts of things without making a bunch of different partitions

Sounds cool....

I just downloaded and burned the GParted iso (I know, I could have used the Ubuntu liveCD) and have booted to it....I'm going to shrink hda1 from 62 to 29 gigs, move hda2 to the left and grow from 9.7 to 29 gigs (for my XP), then create a new Primary Partition with ext3 format at about 12 gigs to use for testing or with Virtual Box.  Will leave Swap at current (3 gig) size...

Will let you know when complete and how things went..

thanks again,

Mick

---

### Post by nml on 2009-04-06
Well....I thought things went well....

I just rearranged my HD as in the above post....GParted completed and I easily booted back into Ubuntu.  Unfortunately, I can't boot into windows....I get to the log on window, then it gets into a restart cycle until I shut it down...any ideas how to get the XP log on back (short of reinstalling the OS)?

Should I need to reinstall XP, do I need to reformat my windows partition, install and then go through the whole reconfiguring the menu.lst?

guess I should have made the partitions I wanted before my installations (live and learn...)

Mick

---

### Post by carml on 2009-04-07
Maybe you need the XP install Cd and choose the recovery option,then use the Live of Ubuntu to restore Grub,selecting the option to Recover the sistem.

---

