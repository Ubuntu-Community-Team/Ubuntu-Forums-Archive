---
title: "switching over"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by brianhillman on 2009-06-02
was going to switch to ubuntu since win 7 beta is expiring whats the best way to do this ? i dont have a external hard drive to back up stuff to. Is it a good idea to create a 25g partition and then run everything from my main partition? or is there another way to only delete Win 7 and install ubuntu without wipeing all data?

---

### Post by XCan on 2009-06-02
You mean that you would like to keep your personal data on the Win7 installation, but get rid of the operating system itself? I assume then that your Win7 install is on one single partition.

In principle, you can as you said create a 25 GB partition for ubuntu and install it there and then every time just mount your Win7 partition. However, I think the best thing to do is to create a ~25 GB partition for Ubuntu / and use ALL of the rest free space to /home (you may need some space for SWAP as well). Then try and move over as much as possible of your personal data to your home folder. Next decision is whether you're satisfied with some data being on the old win7 partition and some on your /home partition. If you're not (and want to take a small risk) you can resize the Win7 partition and merge it with your /home partition and move over the remaining data.

---

### Post by shifty_powers on 2009-06-02
you know that you can download the win 7 release candidate that will work till next year, yes?

---

### Post by Celauran on 2009-06-02
> **shifty_powers said:**
> you know that you can download the win 7 release candidate that will work till next year, yes?

Which will simply postpone the inevitable.

---

### Post by bodhi.zazen on 2009-06-02
> **brianhillman said:**
> was going to switch to ubuntu since win 7 beta is expiring whats the best way to do this ? i dont have a external hard drive to back up stuff to. Is it a good idea to create a 25g partition and then run everything from my main partition? or is there another way to only delete Win 7 and install ubuntu without wipeing all data?

I would resize your windows partition, make a data partition, in install Ubuntu into a new partition.

Ubuntu does not really need more then 10 Gb (plus a swap partition). So make a big data partition, make it ntfs to share with windows.

See also : 

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

