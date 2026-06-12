---
title: "Install Problem with 9.04"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by david.stockham on 2009-09-26
I have had 8.04 installed and wanted to try 9.04. I log in to my XP (dual boot) and cleaned out a bunch of stuff to make more room for Linux partition. I also compressed the files on the HDD to save even more room. Now when I try to install 9.04 (with CD), it runs really slow. I had trouble with ACPI on 8.04 so I chose the work around to even get it to install. I select ACPI=0ff for 9.04. I basically get stuck at the partition screen. I never shows the device information...
Thanks for any help...:)

---

### Post by nmccrina on 2009-09-26
Maybe try the alternate install CD? That's all I can think of :)

If it's a laptop, see if there's any info on it at the Ubuntu laptop compatibility place: [https://wiki.ubuntu.com/LaptopTestingTeam]("https://wiki.ubuntu.com/LaptopTestingTeam"). Hey, maybe you can even create a page for your laptop ;)

---

### Post by oldfred on 2009-09-26
When you said it never showed any info did you give it plenty of time?
When I had 2 160GB sata and one 80GB pata it took about 45 minutes for it to show all the partitions. 
I do not know if your compressed data may make it slow in your case?

---

### Post by david.stockham on 2009-09-26
Yes, it is a laptop..Basically went through the same process I did with Hardy.

---

### Post by david.stockham on 2009-09-26
I appreciate the tips. I will do more research and let you know...

Starting with a fresh CD...

I may go in and unclick the "compress all files" button on my XP load being that it is all I really changes between Hardy and Jaunty...

Thanks all...

---

### Post by Zoot7 on 2009-09-26
Have you tried testing the CD for defects?

---

### Post by david.stockham on 2009-09-27
PROBLEM RESOLVED!

Thanks all for the help...
Started with a fresh CD of Desktop (burned at 8x)
Uncompressed all files on drive
Disabled ACPI (ACPI=off) and LAPCI

Went with defaults for dual boot... Not good. The install has no room for updates. Not sure how I will handle this yet. Maybe fresh install and "advance" partitioning?

Thanks again to all that helped..:)

---

### Post by oldfred on 2009-09-27
When you say the install had no room for updates was it because your XP still has not enough extra room. You should defrag the XP twice before adding Ubuntu.
The other is in side by side install, the slider defaults to 2.5Gb which is just enough to install into but not enough to update or really use. It is assumed that you will move the slider to at least 10GB for a mimimal working instlall.
HOWTO: 2.5 GB System Partition - What Went Wrong? 
[http://ubuntuforums.org/showthread.php?p=7658271](http://ubuntuforums.org/showthread.php?p=7658271)

---

