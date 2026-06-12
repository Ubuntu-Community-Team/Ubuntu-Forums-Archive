---
title: "Crc?"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by Ukai on 2010-12-27
Okay, so I downloaded some .rar files last night of a game I've been looking for for a while, and I tried to un-archive them today and I got the following error on my 10.04 lubuntu and my 9.10 ubuntu: 

Pure Pure -The Story of Ears and Tails-/Game/PUREPURE_DISK_B.bin : packed data CRC failed in volume /home/alex/Desktop/Pure Pure/Pure Pure -The Story of Ears and Tails-.part2.rar

Pure Pure -The Story of Ears and Tails-/Game/PUREPURE_DISK_B.bin - CRC failed

So, how do I fix this issue?  Whenever this pops up, it deletes the folder it was creating.

---

### Post by saptarshighosh on 2010-12-27
CRC stands for Cyclic Redundancy Check. It comes when the HDD has gone corrupt (or a part of the HDD). Try moving the files to another part and extracting them. I also got this error once (in Windows though) and had to replace the HDD.

---

### Post by seawolf167 on 2010-12-27
Just to make sure, try re-downloading the file and unpacking it again (if there is a md5sum use that to verify the download)

---

### Post by Ukai on 2010-12-30
> **seawolf167 said:**
> Just to make sure, try re-downloading the file and unpacking it again (if there is a md5sum use that to verify the download)

Can't believe I didn't try this.  It worked though, problem solved.

---

