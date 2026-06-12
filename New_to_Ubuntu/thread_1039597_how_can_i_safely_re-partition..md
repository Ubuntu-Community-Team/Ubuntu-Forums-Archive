---
title: "how can i safely re-partition."
date: 2009-01-14
forum: New to Ubuntu
---

### Post by niko123 on 2009-01-14
Hello,

I am currently dual booting xp and ubuntu...given that i did not know which OS i was going to use more. I partition both OS's to get half so 18---18 for both OS's. 

BUT my xp is in need of hard drive space and seeing that my ubuntu doesn't even take up much space...i was wondering if there was any safe and correct way that i could give XP more space...without formatting please.

If anyone has any information please let me know.

---

### Post by semi_fiction on 2009-01-14
Boot from the Ubuntu live CD and go to Gparted (System->Administration->Partition Editor.)
From there you can shrink Ubuntu's partition and extend XP's partition into the newly created free space.

---

### Post by jemate18 on 2009-01-14
> **semi_fiction said:**
> Boot from the Ubuntu live CD and go to Gparted (System->Administration->Partition Editor.)
From there you can shrink Ubuntu's partition and extend XP's partition into the newly created free space.

Yup... Gparted makes magic.........

---

### Post by kansasnoob on 2009-01-14
First and foremost map out a plan! If you haven't done so yet you'll want to install gparted to your Ubuntu - **not to change things, but to see what you have!** Any changes will need to be done from gparted, aka: Partition Editor, from your Ubuntu live CD!

A picture's worth a thousand words so:

[ATTACH]99835[/ATTACH]

Of course that may look complex but just ignore everything beyond sda6!

Better yet! Post your own screen shot and we can make a better recommendation!

---

### Post by thane1 on 2009-01-14
Excellent howto on partitioning.
[http://ubuntuforums.org/showthread.php?t=282018&highlight=%2Fhome+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=%2Fhome+partition)

---

### Post by handydan918 on 2009-01-14
> **niko123 said:**
> i was wondering if there was any safe and correct way that i could give XP more space...without formatting please.

No one else seems to have mentioned this, so I will. 
There is NO "safe" way to partition a drive that does not include backing it up first. partitioning is an inherently risky proceedure. If you do it without backing up, your blood is on your own hands.

Ya been told.

):P

---

### Post by laurielegit on 2009-01-14
[SIZE="6"]BACK UP YOUR DATA!!!!![/SIZE]


Five exclamation marks is a sign of madness. But seriously, back up your data. You'll regret it if you don't. If it's documents you could just email them to your self, or set up a gmail account. Gmail currently supports a maximum of around 7gb in it's inbox, so you could get quite a lot stored there in attachments. If it's bigger stuff, like music or films, then invest in an external hard drive. It's a useful piece of hardware, and can help make your disk seem less claustrophobic. Apart from that, good luck.

Laurie

---

### Post by blueridgedog on 2009-01-14
I am one more nut case ...backup for certain.  I have a twenty years of projects, correspondence and files and I don't do anything without two backups.  This weekend I needed to resize a partition and dutifully made two backups on two different removable drives (it takes a while to backup 100 gig - twice).

The resizing went wrong and I ended up opting to repartition.  The first backup failed (the drive was corrupt) and I ended up getting all of my data off of the second backup.  The lesson is that you should always cover your bets.  Good luck.

---

