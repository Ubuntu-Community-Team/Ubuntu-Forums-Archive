---
title: "Handling files from another partition"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by mrdelriego on 2009-08-19
Hi,
 
Like most, i'm new to Ubuntu and really excited about it. Computers haven't been this fun for me since about 2000.
 
I have a Wubi Jaunty installation, sharing C: with Vista. I sorted out many things, mainly those concerning file differences for the amd64 plataform but can't figure ot this one.
 
My files are in a different partition, F:, so i can access them from either OS, however, this is not entirely the case with Ubuntu
- My wallpaper is stored there, when Ubuntu boots, it won't show until i go to Places-> F:, only then it appears as background. Do i have to move it to my Ubuntu home folder in order to have it at startup?
- Some applications, like Picasa and Amarok do not open/recognize files from that partition. If i click on a song, Amarok (the default player associated with mp3) won't do anything. Rythmbox however, can access the location and opens them with no problem.
 
What can i do? Move the files? Stick with the workarounds?
 
Thanks in advance

---

### Post by swoll1980 on 2009-08-19
Do a real install. The way Wubi works is a mystery to me. I have helped guys at my school, by doing a full install for them. They were way happier once they were free of the limitations Wubi had put them under.

---

### Post by oldos2er on 2009-08-19
You need to **mount** the partition before Ubuntu (and any of its programs) can use any files there. There are two ways you can do this; add the partition to your /etc/fstab file, which will mount the partition on boot-up, or mount it after the system is up and running. 

 [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

 There is a nice little GUI app to make mounting partitions a bit easier, **pysdm**. To install it, open a terminal and run
```
sudo apt-get update && sudo apt-get install pysdm
``` Just be careful. Like most system tools, it has the potential to do damage if used incorrectly.

---

### Post by mrdelriego on 2009-08-25
> **oldos2er said:**
> You need to **mount** the partition before Ubuntu (and any of its programs) can use any files there. There are two ways you can do this; add the partition to your /etc/fstab file, which will mount the partition on boot-up, or mount it after the system is up and running. 
 
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
 
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)
 
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
 
There is a nice little GUI app to make mounting partitions a bit easier, **pysdm**. To install it, open a terminal and run
```
sudo apt-get update && sudo apt-get install pysdm
``` Just be careful. Like most system tools, it has the potential to do damage if used incorrectly.
 
Thanks, i'll try it at home, i was offline for  a few days, i apologize.

---

### Post by oldos2er on 2009-08-25
> **mrdelriego said:**
> Thanks, i'll try it at home, i was offline for  a few days, i apologize.

 No worries. Good luck!

---

### Post by mrdelriego on 2009-08-26
problem solved :D
 
Now i have to unmount the recovery aprtition i mounted by accident :P

---

