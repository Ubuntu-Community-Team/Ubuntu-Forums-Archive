---
title: "In over my head"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by USAF_EOD on 2009-06-06
Hey everyone-
Sorry if this issue has been addressed before but I DID try searching in case anyone wants to yell at me. Here's my situation: Recently I purchased a Samsung NC10 netbook preloaded w/ Windows XP. After conversing with a friend who sang the praises of Ubuntu, I decided to give it a shot. My netbook on initial startup gave me an option to set up partitions. Knowing that I wanted to try Ubuntu, I broke it up as follows:

6 GB Windows Recovery (Not negotiable)
95 GB Windows XP
49 GB Second partition

I downloaded and installed Ubuntu Netbook Remix. All was going GREAT and I was very excited. There were things about UNR that I did not like so I decided to try to install Ubuntu Desktop OVER UNR. That's apparently when all hell broke lose. Through I'm sure what can only be called "user error", the desktop install apparently did not go over UNR but created another partition/drive. When I tried to alleviate this through Windows partition manager, I managed to create some error causing the OS loader to not come up. I then reinstalled Desktop again and it is working but I now have only around 3 GB or so. Ultimately, I just want about 100 GB for windows and 50 GB for Ubuntu. If anyone can PLEASE help me, it would be greatly appreciated. I am enclosing a screen shot that may be of assistance. I truly want to learn Linux but at this point, I feel I may have jumped in the deep end before I could swim. Or even float for that matter. Again, all help is greatly appreciated. Thanks to all for your time.

Respectfully,
Joshua

---

### Post by Celauran on 2009-06-06
Probably the easiest solution at this point would be to fire up a LiveCD -- either Ubuntu or UNR, whichever you prefer -- and manually repartition during the install process. You can leave your existing Windows partitions unchanged, delete the mess of partitions the various Linux installs have created, and then create the desired Linux partitions in the resultant unallocated space.

---

### Post by Bucky Ball on 2009-06-06
As Celauran says, this must be done from a live cd as the Linux partitions must be unmounted to work with.

When you are done, rather than two installs, you can try making a 'hybrid'. Maybe start with UNR or Ubuntu (Xubuntu would be more successful than Ubuntu on the netbook though), then load the desktop environments and apps as appropriate from Synaptics. You can do this with a search for 'ubuntu-desktop' or 'kubuntu-desktop' or just load the environments (KDE, Gnome, Xfce ... try some others like Openbox fr'instance).

You can do a search for loading specific apps. My desktop workstation has a Xubuntu install with Ubuntu Studio realtime kernel and apps installed on top of that so to speak. Sort of like a faster Ubuntu Studio with an Xfce desktop environment (my personal favourite).

At the login, you should be able to go to 'Sessions' and choose the environment you fancy - Xfce, KDE, Gnome - whatever environments you have installed.

For two (or three or four!) installs, have a stable install and a 'break and learn' install for experimenting. This means two ***separate*** partitions, of course; one with maybe 8.04 LTS, the other with the latest bleeding edge Manic Marsupial 11.6.6.6 for testing and playing (or another 8.04 that you can experiment on, with the backup of having your stable 8.04 install for everyday use).

:)

---

### Post by USAF_EOD on 2009-06-06
I tried to do the manual partition but it asked for things like mount points etc...  I saw where I could delete partitions and create free space but then I get lost.  Not sure about different types of formatting and sda3 sda5 (Whatever the hell that means).  Would it be possible for someone to PM me a step by step guide?  Sorry for the ignorance and thanks again for the help.

Joshua

---

### Post by Ms_Angel_D on 2009-06-06
First off start by sticking in your live cd and then once the desktop is loaded go system -> Administration-> Partition Editor and delete your linux partitions.

Then to install ubuntu as a dual boot have a look at [this step by step guide with screenshots]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm"), it should get you exactly where you want to be.

The Guide uses Ubuntu 8.04 but you can use 9.04 all the steps are the same. 

Good Luck ;)

---

### Post by lindsay7 on 2009-06-06
When you need to work on a partition or drive in Gparted they must be unmounted. If you right click on one you can unmount it. You can download a Gparted file from their web site and burn it to a cd. It will be a live cd meaning it will boot your computer. When you ues it all the drives and partitions will be unmounted. I find it easier to use Gparted this way better that the Ubuntu cd.

Start with the small partitions inside the larger ones and delete them. Leave the space unallocated. Then do the same for the large partition. When you have done this you should have a large block of unallocated space. You can now set that up as a partiton an format it. Format it as type ext 3. Then install Ubuntu to that partition.

---

### Post by -kg- on 2009-06-06
My advice would be along the lines of what Ms_Angel_D suggested, but with the specs you said you wanted to follow:

> 6 GB Windows Recovery (Not negotiable)
95 GB Windows XP
49 GB Second partition


...my advice would be as follows:

I would suggest that you follow the "How To Partition" link in my signature block first and do a little reading.  This will tell you what you are doing and some of the ramifications and limitations involved.

Now I notice that sda4 is an ntfs partition, and it is outside the Extended partition.  There seems to be around 110 MB of data on it, so I would copy any data you want to save from that (and the other ntfs partitions contained inside the Extended partition) to your sda2 partition before performing the following operations.

As Ms_Angel_D suggested, boot onto the Live CD and launch GPartEd.  You want to delete any partitions you wish to get rid of to make room for the partitions you need to create.

You have a small (7.5 GB) Extended partition which contains your Linux partitions.  The easiest way to deal with this will be to delete it, but you must delete all the Logical partitions inside it before you can delete the Extended partition itself.  In order to correctly install Ubuntu, you will need an Extended partition, especially if you want to experiment with other installations or flavors of Linux.

After you have all but sda1 and sda2 deleted (I assume this is what you want), create an Extended partition surrounding the entire unallocated space on the rest of the drive.  You will be able to create any amount of Logical partitions within this Extended partition.

After you have done this, close GPartEd and launch the installer from the desktop.  You need not reboot to the Live CD to do this; just double click the "Install" icon on the desktop.  When you get to the partitioning section, I personally would launch the Manual Partitioning method and do it that way.

First, you will need to create a swap partition.  You want to put this at the end of the unallocated space as a Logical partition, within the Extended partition you created earlier.  You want to make this partition around 1 1/2 X the amount of RAM you have installed in your computer (this is a safe amount) and format it as swap.

Right-click on the line that says, "Unallocated space," which will be a subset of the Extended partition, and click "New Partition." As I said, you want to create this partition at the end of the free space.  The default is at the beginning (radio buttons off to the right), so you want to click the one for at the end.  Resize it to your desired size and under "Format As" select "swap" from the drop-down menu.  If you are installing Jaunty (9.04), you need do nothing else and create the partition.  If you are installing Hardy (8.04) I can't remember...you may need to mark the mount point as "swap".

Once you have this partition created and saved (it will re-scan the partitions), once again right-click on the "Unallocated space" line and select "New Partition."  Now, since you have around 50 GB of free space, you have several different options at this point.

Some people like to create a separate / (root) and /home partition to make upgrading easier.  You might also want to install different Linux (or other) OSes for experimentation purposes.  Or, you might just want to do a straight up install and forget the complexities.

If you want to straight up install Ubuntu, just use the remaining free space for one big partition, format it as ext3 (should be default) and mark the mount point as "/", which will be root.  Doing it this way will make your /home directory on the root partition.

If you want a separate /home partition, you will need to create the "/" (root) partition as above, but you will have to reduce the size of this partition so you can create the "/home" partition.  How much space you require for the root partition depends on how much software you anticipate loading under Ubuntu.  I have had quite a bit of software loaded under some of my installations, and I never used much over 8 or 9 GB, so 15 would likely be good.  Of course, this depends on your situation and requirements.

After the root partition is created, you would use the rest of the free space for your home partition as above, except you would set the mount point as "/home," of course.

If you anticipate making more than one installation, you will need to leave room for it.  Make your /home partition (or root partition, if you're going to just use a root partition) small enough to contain a reasonable install and leave the rest of the space unallocated.  Then if you decide to install another distro you will have the space to create it in without jumping through hoops resizing existing partitions and the like.

Another note: unless you just *want* to, you don't need much room for your /home partition.  Linux will read and write to an ntfs partition just fine, and you can use your ntfs partition to store and access data from Linux as long as you have enough room on that partition.  If you're just using a root partition, around 20-30 GB would be just fine, and less if you're not going to load scads of software.  Minimum partition size requirements are around 8 GB, so if you're just going to browse the web and get emails (and maybe install a minimal amount of software), 8-10 is fine.

---

### Post by -kg- on 2009-06-06
As an addendum:

If you want to use the new ext4 file system under Jaunty, that is fine.  Just be aware that many other distros aren't using ext4 yet, and as such, their version of GRUB won't detect a /boot that resides in an ext4 partition.  This is the reason I suggested leaving the format as the default ext3 format.

If you decide to go ahead and use ext4, it's OK...after installing another distro of Linux (which might not detect Jaunty and include it under it's GRUB menu) you will need to reinstall Jaunty's GRUB, which will detect it and the other OS as well.

---

### Post by USAF_EOD on 2009-06-07
Thanks to all for the input.  Wound up reinstalling my XP partition which allowed me to delete the other three or four.  Once that was done I installed Ubuntu on the free space.  

NEW PROBLEM:::

Now my wireless does not work.  I have a Samsung NC10 with an Atheros AR5007EG wireless adapter.  I have found a few postings on how to fix this which involves modifying a blacklist or downloading drivers.  I added the proprietary driver to the blacklist but that did not fix the problem.  When I run the live CD, it works fine.  Once I boot from the drive, failure.  Any suggestions?

---

### Post by QIII on 2009-06-07
Did you look at this post?

[http://ubuntuforums.org/showthread.php?t=885847&highlight=Atheros+AR5007EG](http://ubuntuforums.org/showthread.php?t=885847&highlight=Atheros+AR5007EG)

---

