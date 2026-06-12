---
title: "FOUR Questions from  Lenny"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by photocatcher on 2010-12-13
I am about to install Ubuntu 10.10 0n a second internal hard drive on my PC.  The first question I have is should I be online while Ubuntu is being installed or offline?  The second question is when I install it I will be asked about the amount of the hard drive space I want it to use for Ubuntu.  The hard drive is an old one that has XP files still on it.  I do not want to loose them.  What should I do in regards to partitioning the hard drive so that they will not be lost?  The hard drive is an internal 320GB and I will have 240GB of free space to use. What would you recommend me to do?

Thanks in advance.

Lenny

---

### Post by msandoy on 2010-12-13
1. Yes, you should stay online during install, since Ubuntu wants to update repository information and download some language packs.
2 - 4. Before you start the installation process, start up Windows, and do a proper defragmentation. This will hopefully move your files to one end of the disk partition. Then you reboot into the live CD. Start the installer, when asked about partitioning, choose manual. select the windows partition, and resize it. Make it approx 160GB (Just a suggestion). Create an extended partition in the empty space (Not inside the NTFS partition). Inside the extended partition, create a swap partition, approx. two times the size of your installed RAM. Then create a "/" root partition of approx 12-15GB, and the rest you make into a "/home" partition. Remember to set mount points on the correct partitions. ("/" and "/home"). I usually also make a mountpoint for the NTFS partition in "/home/windows", just make sure NOT ot format it, just set the mount point.

Good luck.

---

### Post by Quackers on 2010-12-13
Does the XP partition occupy the whole disc at the moment or just a part of it, with unallocated space after the partition ends?

---

### Post by photocatcher on 2010-12-13
Quackers yes the Seagate 320GB just contains XP files.  It doesn't have too many files on it so I thought the drive would be good to use for Ubuntu rather than partitioning the main hard drive which uses win7.

---

### Post by Quackers on 2010-12-13
If the XP files are in a partition that takes up the whole disc it would need to be resized so that some unallocated space is left for Ubuntu to install into.
You can't install Ubuntu inside the XP partition even if it's mostly free space (unless you are using wubi).

---

### Post by photocatcher on 2010-12-13
Msandoy thanks for the info.  I am using Comcast and lately I am online and then off line a lot. I was thinking that when Comcast had me off line that maybe that would be the best time to install Ubuntu but then I thought I might need to be online to get the latest updates.  On Wednesday a Comcast tech will be here to find the problem as to why I am on and off line so often. 

I do appreciate the time you took to respond to me.

Lenny

---

### Post by msandoy on 2010-12-13
Well, as I said, you "should" stay onlne, but it is not essential. I have done a few installations offline, but just be aware that it might seem to "hang" at approx 90%, since it is searching for repositories, and it will do so until it times out. Just give it time. 
Do a proper defragmantation of your XP drive, and use the Ubuntu resize function as I mentiond in my previous post. You should be fine.

Just thought of something, if you unplug the network cable, and don't connect to wifi, the installation will skip the repository update due to no network. This will reduce the installation time.

---

