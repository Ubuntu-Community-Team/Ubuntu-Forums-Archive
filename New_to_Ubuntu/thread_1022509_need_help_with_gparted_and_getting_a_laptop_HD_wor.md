---
title: "need help with gparted and getting a laptop HD working"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by luke0927 on 2008-12-26
(I want to run windows first this maybe my biggest problem its for my wife so i need to put xp on it) 

OK i have a laptop 160G hard drive that is new that i want to put in a Dell latitude d600 i do not have a floppy so i cant boot to a 98 bootdisk and run fdisk then format c: /s like i normally would.  I found this program called gparted and installed it on my desktop i ran the program and it found the drive as sdc.

it asked to set the disk label and it went off and did its thing now it shows this in the terminal when i run gparted to try and discover the disk

Unable to open /dev/sdc - unrecognised disk label.
Unable to open /dev/sdc - unrecognised disk label.
Input/output error during read on /dev/sdc
Input/output error during read on /dev/sdc


I was able to boot to the xp disk and it saw the disk i told it to put a ntfs partion on thdis. now i told it to format and went of and acted like it was formating and then came back and said it couldn't format it.

I would like to blow this away and start over with gparted and format it in linux and try and get it ready in linux can someone tell me how to format it and set the disk label now that gparted can't see it?

thanks for the help!

---

### Post by -kg- on 2008-12-26
I have just re-written the "How To Partition" section of the Community Wiki:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

This should get you on the right road, and if you have any further questions, feel free to ask.

As you said, you may need to blow the whole thing away and do a fresh reinstall of everything.  If you have the ability, you might want to back up the partition(s) on that hard drive (I notice that the drive is listed as sdc, so I'm assuming that there is more than one physical hard drive installed), completely delete the partition(s), recreate them, then put the data back from the image file you saved of the partition(s)...that is, if you want to save those partitions.

Another consideration:

You might want to download the [GPartEd Live CD]("http://gparted.sourceforge.net/").  This is a standalone, Linux based Live CD that is set up specifically for partitioning operations.  I have used it quite often and it works well.

Other than that, you can use GPartEd from your Ubuntu Live CD for these operations.  This is all included in the How To Partition page(s), as well as backup Live CDs you can download for that purpose.

---

### Post by 73ckn797 on 2008-12-27
If the laptop only has a single HDD you will need to partition using a live CD. 

There are Win boot disk downloads that you can burn to a CD and will allow you to partition and format the drive to the Windows system and then you could install 98. After that repartition to make space for Ubuntu.

---

### Post by luke0927 on 2008-12-27
So there are windows boot disk on CD that will boot to dos?

the hard drive is blank and i have 2 drives in my ubuntu box this is the 3 drive im plugging it into usb...i found how to use fdisk in the command line and blew away the partion and recreated another partion with what i thought was the ntfs filesystem but when i put it back in the laptop it said it was not a recognized file system i used option 86 when creating the file system.....i'll try the things you have mentioned and read the article

---

