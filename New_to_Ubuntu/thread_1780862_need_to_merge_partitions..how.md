---
title: "need to merge partitions..how??"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by smurfgod on 2011-06-12
I'm running 11.04 off an 8 gig usb drive. I'm running the full install cause I didn't know there was a difference between the Live and the full cd. During the install, it made a 4 gig swap. I have turned swap off and commented out the line in fstab, but I want to merge the 2 partitions. I heard it can't be done while there mounted so now I'm lost..lol

Any help?? I'd alos like to go to the Live version if it has a smaller footprint.

Running on a Toshiba Satellite L675D-S7015. Bluray, hdmi, 4 gigs ddr-3. My hdd died so I'm using a flash drive..lol

---

### Post by -kg- on 2011-06-12
By your description, you made a full installation to your flash drive, because you describe that a swap partition was created on it during installation.  This is interesting to me, because I just bought a 16 GB flash drive that I'd like to make a full installation on for portability.

Anyway, to your problem...

You can't really "merge" two partitions like that, with any tool that I know of.  Your root partition is formatted as ext(4, I assume...perhaps 3), while your swap will be formatted as Solaris.  Whether you need swap or not depends on how much RAM you have, and whether you use hibernate.  If you have >1GB of memory (and only use Ubuntu for light-duty operations) and do not intend to use hibernate (stores current RAM contents in swap for reloading), then you probably don't need it.

What you'll need to do is boot with a Live CD (or USB) to do the operations on the flash drive.  What you'll want to do is launch Gparted from the Live desktop, then either resize or delete the swap partition, according to your situation.  Then resize your root partition to fill in the space you created by resizing/deleting the swap partition.

For further information on partitioning operations, read at the link in my signature block.

You know, the smaller USB hard drives are fairly cheap these days, and much easier to use/boot from, let alone having so much more space.  I have a little portable USB hard drive at around 360 GB that cost me around $60 or so.  Just something for your consideration.

---

### Post by smurfgod on 2011-06-12
> **-kg- said:**
> By your description, you made a full installation to your flash drive, because you describe that a swap partition was created on it during installation.  This is interesting to me, because I just bought a 16 GB flash drive that I'd like to make a full installation on for portability.

Anyway, to your problem...

You can't really "merge" two partitions like that, with any tool that I know of.  Your root partition is formatted as ext(4, I assume...perhaps 3), while your swap will be formatted as Solaris.  Whether you need swap or not depends on how much RAM you have, and whether you use hibernate.  If you have >1GB of memory (and only use Ubuntu for light-duty operations) and do not intend to use hibernate (stores current RAM contents in swap for reloading), then you probably don't need it.

What you'll need to do is boot with a Live CD (or USB) to do the operations on the flash drive.  What you'll want to do is launch Gparted from the Live desktop, then either resize or delete the swap partition, according to your situation.  Then resize your root partition to fill in the space you created by resizing/deleting the swap partition.

For further information on partitioning operations, read at the link in my signature block.

You know, the smaller USB hard drives are fairly cheap these days, and much easier to use/boot from, let alone having so much more space.  I have a little portable USB hard drive at around 360 GB that cost me around $60 or so.  Just something for your consideration.

So just boot a live cd, delete the swap and extend the root to fill the void?? You mentioned hibernation...Ever since I deleted the swap, after i open my laptop, it goes to a black screen with blue pinestripes...could that be why??lol

---

### Post by oldfred on 2011-06-12
Pros & cons of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

The liveCD is not update-able. You can add persistence to allow you to save some data but you cannot update system as it still is the liveCD.

I installed to a 16GB flash but made / (root) 8GB and the rest as data. Turned off as much writing as possible. I also used gpt since it was recommended for SSDs and a flash drive to me is just a poor man's SSD (or slow version).

Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

