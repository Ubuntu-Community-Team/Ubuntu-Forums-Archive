---
title: "need help with partition"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by skilgannon82 on 2011-05-15
i created a 50 gb partition to dual boot ubuntu from and when i run ubuntu from my usb i go to install it but the partition i created is not there please somebody help me ive been trying to install ubuntu for two days now and its doing my head in
i have an i5 hp pavillion g6 laptop with 64 bit windows 7 and a 1gb  radeon graphics card if that helps with my problem

---

### Post by skilgannon82 on 2011-05-16
bump

also i have read every tutorial i could find and i cant seem to find anything specific to my problem 
im losing my mind please help me

---

### Post by Quackers on 2011-05-16
How many primary partitions were in use on your system before you tried to create another?
Have a look in Disk Management in Windows, or in gparted on the Ubuntu live cd.

---

### Post by skilgannon82 on 2011-05-16
there was 4 i think and some guy told me to shrink the main partition so i did and created a 50 gb volume so i could install ubuntu on it and it seemed to work but when i go to install ubuntu while im running it from usb the volume i created does not show up and i dont know if i should mess with the ones that do show up

---

### Post by Quackers on 2011-05-16
Regardless of their size, on an mbr partitioned disc (and most are) you can only have 4 primary partitions. If your attempt to create a fifth has been successful Windows will have changed its partitions to dynamic disks instead of simple volumes. This is ok for Windows, but a disaster if you want to install any other operating system.
What does Windows Disk Management console report for your partitions? Post a screenshot if unsure.

---

### Post by skilgannon82 on 2011-05-16
it definitely did make it a dynamic drive i tried to make it a simple drive but after i had finished it it said it was a dynamic drive and that no other OS could boot from it but the current one (im assuming windows 7) i followed instructions from another guy who told me what to do and that his was a dynamic drive also because there was no other option but he reckons his ubuntu loads fine but i cant even install mine
i feel like ripping my hair out this is so frustrating

---

### Post by Quackers on 2011-05-16
Post 5 in the thread below has a link for converting back, though I have not heard any encouraging stories, myself.
[http://ubuntuforums.org/showthread.php?t=1669910](http://ubuntuforums.org/showthread.php?t=1669910)

The only other option that I'm aware of is to re-install Windows 7 (from recovery discs/partition if necessary). Then if 4 partitions are used again you will need to delete one then create an extended partition in its place (or resize the C: partition as well to create more space and make an extended partition there).
Either way, when finished you must have no more than 3 primary partitions and an extended partition, into which you can then install Ubuntu.

I would write to HP thanking them for their ridiculous decision to use all 4 primary partitions for installing a system that needs only 3 at the most. They have ruined your day!

---

### Post by srs5694 on 2011-05-16
The Windows [EASEUS]("http://www.partition-tool.com/personal.htm") and [Partition Wizard]("http://www.partitionwizard.com/") programs can supposedly convert from "dynamic disk" to "basic disk" format; however, I've never used either program, so I can't comment from personal experience. If you can't get these to work and are on the verge of re-installing everything, then you might try deleting all the partitions and using the Linux [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") program to "recover" the partitions as regular partitions. This isn't guaranteed to work, though, so be absolutely sure you've backed up all your important data first.

In the future, don't use the Windows partitioning tools for anything, except perhaps resizing the Windows boot [noparse](C:)[/noparse] partition. As you've discovered, these tools are unreliable.

Quackers' suggestion of complaining to HP is worthwhile. Manufacturers will keep pulling nonsense like this as long as people don't complain. OTOH, this specific issue is unlikely to be a problem for much longer; before too long, MBR limitations will force a shift to GPT, which doesn't suffer from the 4-partition limit of MBR. Of course, I'm sure they'll figure out a way to mess up GPT -- in fact, Apple already has, with the ugly and dangerous [hybrid MBR]("http://www.rodsbooks.com/gdisk/hybrid.html") it uses to enable Macs to dual-boot with Windows.

---

