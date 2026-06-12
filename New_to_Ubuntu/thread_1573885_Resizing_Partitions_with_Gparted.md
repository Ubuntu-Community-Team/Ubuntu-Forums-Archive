---
title: "Resizing Partitions with Gparted"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by HackSoul on 2010-09-13
New to Linux after many years.  Installed Ubuntu next to xp on a laptop to try and save xp installation.  No hope for old xp install.  Realized Ubuntu served needed purpose far better than old xp.  Booting from live cd using gparted to resize partition.  Havn't a clue how to resize linux partition to include unallocated space from old xp install after spending many hours perusing forums and the like.  Have already spent many hours getting to know linux in it's current ubuntu form and configuring laptop for 9 yr old child.  I do not want to reformat the hard drive and reinstall ubuntu, but for the life of me can't find clear instructions on using the gui frontend of gparted to complete the task.  Included is a screenshot from gpartded.  Any option to move, unmount, or resize ubuntu partition is greyed out.  Any help?  If I am asking for help in the wrong area. . . apologies. . .

---

### Post by srs5694 on 2010-09-13
First, realize that any partition resizing or moving operation is inherently risky. Power failures, bugs, undetected damage to the filesystem, and other problems can all cause data loss. Back up your important data before proceeding.

Second, I believe you should click the "+" sign on the far left side of the partition list to show the contents of the extended partition. When you do this, you'll be able to right-click the swap partition and select an option to deactivate swap space, which is currently active and preventing any changes to the extended partition.

Once you've done this, you should be able to select /dev/sda2 and resize it so that it covers the whole disk, then move and/or resize /dev/sda5 (the main Linux partition). You can either resize it to take the whole disk or create a new /home partition without resizing the main Linux partition. Given the risks of moving or resizing a partition, the latter is probably a safer course of action, but it will also take more effort and understanding to pull it off. [This article,]("http://www.ibm.com/developerworks/linux/library/l-partplan.html") although rather elderly, describes the basic process.

Once you've done all this, it's conceivable you'll need to re-install your boot loader. Post back for details if you have problems booting, or check for options to do this in the install disc. (I'm not sure if there's a simple option for restoring a system to bootability in a menu somewhere, but there might be.)

You might also want to check out my recent two-part series on partition resizing: [Part 1]("http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html") and [Part 2.](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

---

### Post by eriktheblu on 2010-09-13
Looks like you have an extended partition containing your primary (/) partition.

Try to expand the extended partition using the + sign next to /dev/sda3. You should see /dev/sda5, unformatted space, and a swap contained within it. Make sure /dev/sda5 is unmounted, then turn off your swap, then unmount /dev/sda3 (the swap is probably what is preventing you from resizing).

Once you get everything unmounted, it should be fairly self explanatory.

It looks like you have a small swap partition, so you may experience performance problems when you disable it. You could potentially circumvent this by creating a new swap (roughly the same size as system memory) at the beginning of your drive.

---

### Post by ajgreeny on 2010-09-13
srs5694 has got a few things slightly muddled, so let's try to put it right.

I agree wholeheartedly about backing up all your important data as any partition activities are inherently dangerous, though having said that, I have used gparted many, many times and never had a problem (touch wood!)

So, using gparted on the live CD, click on the + sign of sda3, and I think you will see sda5, which is your ubuntu OS and sda6, which is probably the swap partition, though it is not shown in your screenshot.  You may need to right click on the swap partition and choose "Swapoff".

Now grab the left hand edge of sda3 (blue in your screenshot) and pull it all the way back left to take the full space of the disk and fill the full 59.27GB presently unallocated, and similarly at the right hand edge, where there is a small area also unallocated.  That activity will be queued up in the bottom panel, but I would go ahead and accept that to give a complete disk sized extended partition.  This is no problem for a linux distro which will boot from a logical partition within an extended partition with no difficulty.

Having done that, you can now click on the left hand edge of sda5 and pull that back fully left to fill the empty space, or more easily and safely, simply make a new partition in ext4 format, and use that for all your data files.  The new partition can be mounted at boot time easily with a simple edit of /etc/fstab.   It is even possible to use that new partition as a new dedicated /home partition if you prefer, see [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) for details.

You will also need a swap partition, probably the non showing sda6 on your disk, and it would be better if it were bigger than the current size, which working from partition and disk sizes shown, I calculate to be smaller than is needed.

Come back again if you need more info on all of this, which may sound complicated but is actually easier than it sounds.

---

### Post by HackSoul on 2010-09-13
Clicking swapoff was the missing ingredient!  That one step wasn't mentioned any place I looked.  Worked like a charm after that.  Thank you to all who responded.  Helpful people and open source software make me a happy panda!  :D

---

