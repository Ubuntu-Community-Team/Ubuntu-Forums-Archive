---
title: "re-size folders?"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Paul T. on 2009-06-17
According to disk usage analyser, my 'home' folder is already 71% full, and I still have more music/video files to load, there's 20+ Gb of space available, how do I resize space allocated to folders? (See attatched screen shot)

Paul.

---

### Post by kttyshadow5 on 2009-06-17
The best I could find for you is this [http://www.go2linux.org/how-to-move-home-directory-to-another-partition](http://www.go2linux.org/how-to-move-home-directory-to-another-partition)
It looks like you might have to give your home folder its own partition... :-k

---

### Post by Paul T. on 2009-06-17
Not sure if I can create another partition, already have 5 partitions + 1 hidden recovery partition. (EeePC904 with XP) :confused:

---

### Post by mcduck on 2009-06-17
> **Paul T. said:**
> According to disk usage analyser, my 'home' folder is already 71% full, and I still have more music/video files to load, there's 20+ Gb of space available, how do I resize space allocated to folders? (See attatched screen shot)

Paul.

That is not telling that your /home would be 71% full. It's telling that 71% of *used disk space* is used by /home.

Directories don't have any size limit (at least by default) , so unless your /home is located on separate partition the amount of space available there is the same as in any other directory. Which is the size of the partition.

edit: Actually, if you look at your screenshot you can see the text: "Total filesystem capacity: 31.8GB (**Used: 7.6GB** available: 24.3GB)". And the reported disk usage for your /home is 5.3GB, which is 71% of the total 7.6GB of used disk space.

---

### Post by Paul T. on 2009-06-17
> **mcduck said:**
> That is not telling that your /home would be 71% full. It's telling that 71% of *used disk space* is used by /home.

Directories don't have any size limit (at elast by default) , so unless your /home is located on separate partition the amount of space available there is the same as in any other directory. Which is the size of the partition.

edit: Actually, if you look at your screenshot you can see the text: "Total filesystem capacity: 31.8GB (**Used: 7.6GB** available: 24.3GB)". And the reported disk usage for your /home is 5.3GB, which is 71% of the total 7.6GB of used disk space.

Ahh I see now, thx for that info, much appreciated.  :D

---

