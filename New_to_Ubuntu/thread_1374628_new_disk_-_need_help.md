---
title: "new disk - need help"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by anewguy on 2010-01-07
I've gotten a larger hard disk and will be installing both Windows and Ubuntu to it.  I understand putting Windows on first, then Ubuntu, so that grub is okay, etc..  But I have something additional I need to do:  my old drive is going into another PC, but it is what I currently have 9.10 installed and updated on and run off of.  I'm thinking it's probably going to have something to do with booting up on the LiveCD, then somehow copying the partitions from my old drive to the new drive, but I have no clue how to do that in Ubuntu.  Will I have to copy the root file tree, or can I copy partitions somehow even if they are different sizes?  I also have a separate home partition on the old drive I will need to copy over as well.

Any help for another of my dumb questions would be greatly appreciated!

Thanks in advance!

Dave :)

---

### Post by unmole on 2010-01-07
-You can backup your current installation using [remastersys]("http://www.geekconnection.org/remastersys/") and make a custom cd image.

-Then use this [guide]("http://www.psychocats.net/ubuntu/separatehome") to create a separate home partition and copy over your content to your new HD.

-Finally,install from your custom iso and be sure to select the /home partition during installation. 

There are probably other ways such as cloning your HD but I doubt that is what you want to do.

---

### Post by lkraemer on 2010-01-07
Dave,
I have successfully used Clonezilla's LiveCD to copy drives or partitions
in the past.  [http://clonezilla.org/](http://clonezilla.org/)  

I just purchase a larger drive (typically IDE), plug it into an Open
connector on my Secondary IDE Cable.  Make sure the drive is recognized
in the BIOS.  I can then boot a LiveCD of Gparted, select the new Drive
(making sure the size matches the new drive) and partition as needed.
(There is a MAXIMUM of only FOUR Primary Partitions allowed on any
Physical drive.......but you can make an extended Partition, and add
Logical Partitions as needed.....I just elect not to use this method).
I use:
Partition #1 = Windows  ~as needed
Partition #2 = /     ~10 to 15 Gig
Partition #3 = /home    ~ Rest of available space
Partition #4 = Linux-Swap    ~ Two times your RAM

Windows should be installed first, because it wants to be the ONLY OS
installed. (There are ways to install it after Ubuntu, but it's easier
to install Windows first.)  After Windows is installed, just copy the
Partition from old Drive to NEW Drive.  After you have the Partitions
copied, you can expand the Ubuntu Partition and setup Grub (or Grub2).
(I haven't used Grub2 yet after copying because I use 8.04.3)

There is a -r switch and -g switch in Clonezilla that you can check out.

Use the Spacebar to select SOURCE, then DESTINATION.
UNSELECT the -g-auto (write grub) and then SELECT the
-e Resize Filesystem to fit size in Target Partition.
(Newer versions use -r Resize Filesystem to fit size in Target....)
When you are asked "Do you want to clone the Bootloader?"
answer YES.  If for some reason the -e (now -r) option doesn't work
correctly, you can always load gparted and manually resize the partition.

Finally, Insert the NEW Drive as MASTER on the Primary IDE Cable and
Boot to test everything.

You should also be able to copy the partitions with Gparted, but I haven't
used that either.

You could always do a FRESH install of Ubuntu and then copy your data files
from the old drive to the new drive.  At times I think this is best to purge
all the un-needed software.  Just install what you need in the FRESH install.
In just a few months Version 10.4 will be released and it will be LTS.

lk

---

### Post by anewguy on 2010-01-09
Thanks for the replies, everyone! 

Turns out it is a mute point for me right now.  My old motherboard supports SATA drives but doesn't allow booting from them.  Linux sees the drive after boot, and for Windows you have to do the F6 thing during install and install the drivers.  So, down the tubes on this.

On a side note, I bought a used 200GB SATA 7200RPM Maxtor drive off EBay, which I am now selling.  If anyone is interested in it, please see:

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=220537797795]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=220537797795")


Note that I'm only trying to get back what I paid (I won the auction for only $17.71 plus $10 shipping - that's all I want out of it.  The reserve price is even lower.  I never tried the drive as I found the SATA problem with my motherboard when installing a SATA DVD/RW which I returned to Micro Center last night.  If you buy the drive and there is a problem you can return it to me and I'll refund all of your money.

Thanks again!

Dave :)

---

### Post by lkraemer on 2010-01-10
Dave,
You can try booting from the SATA by copying the SATA drivers to floppy
and booting from CDR with the floppy inserted so Windows can locate the
SATA Drivers.

Also, another option is to Slipstream your version with the latest
Service Pack SP3, add the Latest Hotfixes, and add the SATA Drivers.
If you want more information on doing this let me know.  I've sucessfully
done an older SP2 OEM Version of XP.

lk

---

