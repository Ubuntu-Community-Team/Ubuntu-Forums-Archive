---
title: "partition help"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by skyeric on 2010-05-13
i want to partition my hard drive but having problems, got onto disk utility and selected format drive but then it says 'one or more partitions are busy on /dev/sda'. i only have ubuntu 10.04 installed on this computer atm any help appreciated?

---

### Post by ratcheer on 2010-05-13
Are you sure you want to reformat your drive? You will lose everything that is currently on it.

If you do, boot to a live CD and run Gparted (should be in System >> Administration).

Tim

---

### Post by skyeric on 2010-05-13
i dont want to completely format it, i want to create a new partition that i can install a different OS on?

---

### Post by nothingspecial on 2010-05-13
> **skyeric said:**
> i want to partition my hard drive but having problems, got onto disk utility and selected format drive but then it says 'one or more partitions are busy on /dev/sda'. i only have ubuntu 10.04 installed on this computer atm any help appreciated?

You cannot partition/format a mounted drive. So like racheer said you have to do it from the live cd, (or seperate file system) because if you are using your computer then it is mounted.

---

### Post by skyeric on 2010-05-13
okay cool so if i boot from the live CD i can partition without blanking what I already have yea? just want to make sure before I go ahead with this...

---

### Post by nothingspecial on 2010-05-13
Back everything up first.

Yes, you can create a new partition without loosing everything. I`ve done it on all my computers..........but accidents can happen.

---

### Post by skyeric on 2010-05-13
okay i'll go for it now will report back ina bit, already got it backed up onto my windows laptop so thats fine

---

### Post by SKhan on 2010-05-13
don't forget to back-up your important data before attempting to format.

---

### Post by skyeric on 2010-05-13
all working fine :)
made a new partition and all data in the original is the same.
thanks a lot for the help guys,
Eric

---

### Post by manocools on 2010-05-14
Windows XP Professional supports  two types of disk storage: basic  and dynamic. Basic disk storage uses partition-oriented disks. A basic  disk contains basic volumes (primary partitions,  extended partitions, and logical drives)................[continue reading clicking here  ]("http://619tips.blogspot.com/search/label/Convert%20To%20Basic%20And%20Dynamic%20Disks%20In%20Windows%20Xp")

---

