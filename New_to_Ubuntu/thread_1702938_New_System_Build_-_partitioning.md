---
title: "New System Build - partitioning"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by PZJM on 2011-03-08
Hey folks, I will be converting my windows systems to Ubuntu.  I've purchased the Beginning Ubuntu book and tested Ubuntu over the past several years and now I'm ready.  However, I am stuck on partitioning my terabyte hard drive.  I am building a new machine this weekend and it will be mainly used for 1) video editing, 2) photo management/editing, 3) music.  Eventually, I will install LAMP and do some web development testing.

I've read numerous documents regarding partitioning but have yet to find one that documents a setup for video editing.  If possible, could someone review my initial setup and let me know if this looks ok?

Here are my current thoughts:

1) boot partition - 500megs (ext4)
2) root partition - 20 gigs (ext4)
3) home partition - 150 gigs (ext4)
4) swap partition - 4/5 gigs (swap)
5) media partition - what ever is left 800+ gigs (ext4) 

The media partition will be where I do most of my video editing, photo management and music stuff.  Does this look correct?  Should I use ext3 instead of ext4?  Any help would be greatly appreciated.

I plan on building a 64bit system.  The specs are as follows:

- BIOSTAR A880G+ AM3 AMD 880G HDMI Micro ATX AMD Motherboard
- AMD Athlon II X3 450 Rana 3.2GHz Socket AM3 95W Triple-Core 
- G.SKILL Ripjaws Series 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10666) Desktop Memory Model F3-10666CL8D-4GBRM
- PowerColor AX4650 1GBK3-H Radeon HD 4650 1GB 128-bit DDR3 PCI Express 2.0 x16 HDCP Ready Video Card

Thanks...

---

### Post by Daveth on 2011-03-08
why so complicated? What is wrong with root, home, and swap, all ext4? Separate /home is a must, but i do not see why you need a separate media partition as opposed to a media directory under home. Or am I missing something?

---

### Post by PunkLV on 2011-03-08
I would recommend:
100gb for /home ext3
4gb for /swap (in case you do not use hybernation then 1gb)
150-200gb for /media storage ext2 (.mp3 .jpg and such)
700gb for /home/yourwork ext4

---

### Post by PZJM on 2011-03-08
Thanks for the comments.  The reason I was going to choose a media partition was because of some of the documentation I've read including the one in Ubuntu.  They state your home partition should be a max of 250 gigs.  That confused me because hard drives now-a-days are large.

So, it looks like I don't need a boot partition?  Is this taken care of in the root partition?

Thanks for the help.

---

### Post by PunkLV on 2011-03-08
You most likely don't "need" a separate partition for /boot and /root.
And the 250gb limitations for /home -- first time I hear this. Can not confirm it is wrong, yet extremely doubtful.

---

### Post by PZJM on 2011-03-08
Once again, thanks for the suggestions.  Also, could you please explain why ext2 instead of ext3 or 4?

By the way, I can't wait to get away from Windows!!! My kids were the test with Edubuntu and they love it.

---

### Post by PunkLV on 2011-03-08
Ext2 basically is the same as Ext3 but without journaling, which makes it perfect for storing (not moving/editing/etc) non-system data. 
You may want to read [http://www.troubleshooters.com/linux/ext2toext3.htm](http://www.troubleshooters.com/linux/ext2toext3.htm) short and to the point.

---

### Post by grahammechanical on 2011-03-08
I have just discovered that ext = extended. So ext2 = second extended file system, ext3 = third extended file system, ext4 = fourth extended file system.

Regards.

---

### Post by srs5694 on 2011-03-08
> **PZJM said:**
> I've read numerous documents regarding partitioning but have yet to find one that documents a setup for video editing.  If possible, could someone review my initial setup and let me know if this looks ok?

Here are my current thoughts:

1) boot partition - 500megs (ext4)
2) root partition - 20 gigs (ext4)
3) home partition - 150 gigs (ext4)
4) swap partition - 4/5 gigs (swap)
5) media partition - what ever is left 800+ gigs (ext4) 

I agree with Daveth that there's probably no need for a separate media partition. I might separate it out on a dual-boot system or if I had specific filesystem needs, but I don't think it'll do you much good in this configuration. A separate /boot partition is also unnecessary in most cases, although it can be handy if you wanted to use certain types of RAID or LVM configurations.

I'd increase the swap partition to 1-2x times your system RAM, or 4-8 GiB in this case. Chances are you won't be swapping much, but having at least as much swap as you have RAM ensures that you'll be able to use the hibernate (suspend-to-disk) feature if you need to, and it can be useful insurance in case your RAM needs grow significantly in the future or spike briefly because of some unusual one-time needs.

> I plan on building a 64bit system.  The specs are as follows:

- BIOSTAR A880G+ AM3 AMD 880G HDMI Micro ATX AMD Motherboard

FWIW, my experiences with BIOSTAR motherboards have been uninspiring. One (which I'm still using) is very sluggish in its BIOS checks if any USB storage devices are attached at boot time, and it's just been generally a bit on the flaky side (occasional freezes, networking errors, etc.). Another (which I no longer own) was just generally a little flaky and had problems with GUID Partition Table (GPT) disks that were created exactly to spec, although it was OK with GPT disks with a minor and common deviation from spec.

---

### Post by JKyleOKC on 2011-03-08
Note that the /media file system, in Ubuntu and its relatives, is one that has some special properties. In particular, any folder mounted there will show up in "Places" automatically.

For your planned use, I'd change the name of that one to /data, which has no special meaning to Ubuntu.

Otherwise your plan looks good...

---

### Post by PZJM on 2011-03-09
WOW - Thanks for all the help.  I'm impressed with the quick and thoughtful responses.  I will take all your suggestions into consideration.  I'm hoping my transition from Windows to Linux will be a smooth one.

As for BioStar, I've already ordered the motherboard.  I currently have 2 and they are performing ok (nothing great).  Hopefully I will get a diamond in the rough?

Once again Mahalo....

---

