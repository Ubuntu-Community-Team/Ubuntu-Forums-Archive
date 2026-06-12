---
title: "Merging USB Partitions"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-04-03
I was about to creat a start-up USB with Ubuntu 9.04 Beta when this came up. When connected my 4.1Gb USB, two icons appeared in my screen: "4.1 GB Media" and "3.9 GB Media". I installed the Gnome Partition Editor from Add/Remove Applications to incestigate. 
Interestingly, it reads that there 2 volumes in this: 3.77Gb and 3.6Mb. I was trying to merge them together,but it won't let me. The 3.77Gb is fat32 file system while the 3.6Mb is ext3. I thought of reformatting, but it won't let me, either.

How do I fix this?

Thank you for your time.

Take care,
RedStarYellowSun

---

### Post by semitone36 on 2009-04-03
Can you delete either of the partitions?

---

### Post by semitone36 on 2009-04-03
Actually I just thought of something...  Im not TOO experienced with editing partitions but I do know that you arent allowed to edit partitions on a device that is in use.  Maybe try unmounting your stick and then Run GParted?

I dont know if GParted will still be able to access your USB stick but it might be worth a try.

---

### Post by RedStarYellowSun on 2009-04-04
It worked!
I used the Partition Edotor after unmounting the USB. I deleted the 3.6Mb and expanded the 3.77Gb and the whole USB is united. No more second Icon when I plug my USB in.

Thank you!

Take care,
RedStarYellowSun

---

