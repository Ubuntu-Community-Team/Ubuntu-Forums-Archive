---
title: "Problem With HDD partitioning?"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-05-15
Actually i am facing this in both ubuntu and windows , As u can see in the image there is a 1.83mb unallocated spca in between 2 partition preventing them from expanding How to get rid of this so that i could merge 2 partition abobe and below it .I tried for  matting but ubuntu was unable to do so.

---

### Post by MegaJim on 2009-05-15
Learn to ignore it.

It happens for various reasons to do with logical partitions, none of which are a danger to the disk.

You can try to move the partitions to fill the gap using something like parted magic, but considering the time taken to perform an operation like that against the space you'd gain, you are better off ignoring it.

---

### Post by ravi_buz on 2009-05-15
is that a bad sector

---

### Post by MegaJim on 2009-05-15
nope, its just annoying, see this explanation for why these can occur: [http://ubuntuforums.org/showpost.php?p=6436891&postcount=6](http://ubuntuforums.org/showpost.php?p=6436891&postcount=6)

---

### Post by renegade_phoenix on 2009-05-15
Hi I am a newbie but I wish to offer my observation  I have XP and win 7 and Jaunty on seperate partitions on a  a single drive....I have that space on my drive also, it was set by windows when it installed the OS's. When I did the installs on a new formatted partition it requested an 8mb space to "write" to I think it is to hold the Windows bootloader.  Hope this helps, Phil

---

### Post by NHArticleTen on 2009-05-15
> **ravi_buz said:**
> is that a bad sector

It's doubtful that portion of your platter is damaged but it might be.

It's more likely that the partitions are formatted with differing file systems and that sometimes causes a space to be left between partitions.

If you can't live with it that way you might back everything up and DBAN the drive and reinstall, but be forewarned that if you're going to put all the same stuff back on(with the different file systems) then you'll probably see the same issue after hours of fiddling with it.

Throw Windoze out the window...make Linux not war!

enjoy!

---

