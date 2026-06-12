---
title: "Partition probs while installing windows"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by vivaldibabe on 2009-11-27
Hi-

Long story short, I love ubuntu but lack the comp prowess to be able to function well on it. Ergo, I decided to uninstall my Jaunty and install xp so I can upgrade to 7.

Problem is, windows has decided it won't install because there's something wrong with my partitions... I've tried blowing the partitions using the ubuntu install cd, but to no avail.

So now I'm free falling. Is there any other way I can completely clean/format my partitions so I can install windows without it complaining at me?
Is there something I'm missing in this process?

Thanks for reading. Hope you ate lots of pie this Thanksgiving. :D

---

### Post by Aearenda on 2009-11-27
No pie for me, wrong country :-(

When you install from a standard Windows CD, you can delete all the partitions and then get it to create its own. Have you tried that? Or are you using some funky manufacturer's recovery system?

---

### Post by Logistics64 on 2009-11-27
Are you saying that the Windows 7 installer is telling you that your partitions are messed up and the install can't continue? Try running a Live copy of gParted or just boot into your Ubuntu live CD and format the whole drive and merge it all into one partition. Let me know if that works, it did for one of my buddies.

---

### Post by Bartender on 2009-11-27
The Windows installer wants to see a primary NTFS partition.  I can just about guarantee that's your problem.  Go back in with GParted and create a primary NTFS partition out of part or all of the drive and try again.

---

### Post by vivaldibabe on 2009-11-27
I tried resetting the partitions with my ubuntu cd, but it wouldn't let me save. =\
Hmm, gparted, you say? I shall try it. Thanks.

I'll keep you updated on that. =)

---

