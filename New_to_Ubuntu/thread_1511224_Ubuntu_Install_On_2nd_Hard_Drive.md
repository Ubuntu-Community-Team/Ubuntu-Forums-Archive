---
title: "Ubuntu Install On 2nd Hard Drive"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by gordon3056 on 2010-06-16
I have been trying to install Ubuntu 10.04 on my second 80GB Seagate hard drive but the partition manager in setup doesn&#8217;t recognise the drive only the primary c: drive is it possible to do this using the installation disk and have a working boot manager.

---

### Post by marty1011 on 2010-06-16
Correct me if I am wrong. Did you select the 2nd hd? It should be under something like /dev/sdb or /dev/sdc. /dev/sda is your primary hd.

---

### Post by gordon3056 on 2010-06-16
I’ve got a 320 GB primary which I don’t want to partition for various reasons and an 80GB logical which isn’t recognised. On one install my external 500 GB drive showed up however?

---

### Post by spotted zebra on 2010-06-16
i feel like you may have to set up a dual boot to get this to work correctly. i haven't done one in years but i am sure if you searched here or google you could find a step by step tut on how to get it done. 

i am not totally sure on this but it is worth a shot.

---

### Post by gordon3056 on 2010-06-16
I’ve done a dual boot a couple of months ago that’s ok but how do I get the system from the disk to my chosen drive if it doesn’t show up?

---

### Post by oldfred on 2010-06-16
Was this drive ever in raid set or settings? The raid metadata prevents the partitioner from changing it.

Do NOT run this if you have raid.
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by gordon3056 on 2010-06-16
Wow with five cups of Ubuntu I’m going have to give this some thought I’ll plough through it tomorrow evening it’s getting late here. I’ll post resolved if I get a result thanks.

---

### Post by corncob on 2010-06-16
When the partition manager comes up, did you select "use entire drive"?  It should then show you the available drives.  Its a drop down menu, I think.

---

