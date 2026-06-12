---
title: "2nd harddrive installation question"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by conman5 on 2009-10-30
Hello,

A while ago, i posted here about installing Ubuntu on a HD that already had an OS, and learned that if Ubuntu detects another OS, it will offer to install a boot controller that will ask me which I want to boot.

My question now deals with installing on my system. Currently, I have XP with all everything set up the way I want it. I also have another HD I can install, and on it I want to install a Microsoft OS (either vista or 7, just to try them), and then Ubuntu. I guess, Im asking how should I go about these installations without messing up my current XP install?

Thanks,
Conman5

---

### Post by N4zgu1 on 2009-10-30
I think you should make a ntfs partition for windows first and then install windows on it (I recommend you to install 7), then you can install ubuntu on the remaining space. 

The reason for this is that windows doesn't recognize linux but linux does recognize windows and allows you to boot it.

---

### Post by conman5 on 2009-10-31
So, I just tell the Win7 install to go to the 2nd HD?

Then I just change which HD to boot from in bios?

---

### Post by N4zgu1 on 2009-10-31
Yes, but I suggest you to partition first with the ubuntu livecd

---

### Post by conman5 on 2009-10-31
So, you are saying that I should make the NTFS partition Win7 will use the the Ubuntu CD? Then install win7 and after, ubuntu.

One other thing, since I am a noob when it comes to mutli-OS. To protect my current XP install, should I unplug the drive, then plug it back in once the win7 install is complete?

Thanks for your help

---

### Post by mapes12 on 2009-10-31
I would suggest you have a look through this link before you role your sleeves up and make any changes: [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by jmundinger on 2009-10-31
> **conman5 said:**
> So, you are saying that I should make the NTFS partition Win7 will use the the Ubuntu CD? Then install win7 and after, ubuntu.

One other thing, since I am a noob when it comes to mutli-OS. To protect my current XP install, should I unplug the drive, then plug it back in once the win7 install is complete?

Thanks for your help

I have an older Dell desktop.  I have xp installed in one partition on the first hard drive with the other partitions on that disk formatted ntfs and used for data storage.  The computer has a second hard drive.  One partition has a second copy of xp installed (it is there in the event of a crisis), one partition is partitioned ntfs and used for data.  The largest partition on the second disk had been ntfs and used for redundant backup.  When I decided that I also wanted to install Ubuntu on this computer, I deleted that partition.  I then ran the Ubuntu live cd and installed it to the largest unallocated space on the second hard drive.

I don't know windows 7.  But, I suspect the procedure would be similar (except that you can't create a new partition within an existing partition with disk management in xp).  Install the two windows OS first and then install Ubuntu.

---

### Post by jmundinger on 2009-10-31
> **conman5 said:**
>  Then I just change which HD to boot from in bios?

No.  You don't have to edit the bios.

Installing Ubuntu will also install GRUB which will override the MBR.  When the computer boots to the first hard drive, you will see the GRUB menu.  It will include the option to boot into one or Ubuntu kernels as well as a couple of Ubuntu administrative options.  In addition, the menu will include a windows option.  If you select the windows option, the screen will then switch to the MBR and that screen will give you the option to select either of the windows installations.  You can edit GRUB with startup manager to select the default OS.  You can edit the MBR with msconfig to select the default windows OS.

---

