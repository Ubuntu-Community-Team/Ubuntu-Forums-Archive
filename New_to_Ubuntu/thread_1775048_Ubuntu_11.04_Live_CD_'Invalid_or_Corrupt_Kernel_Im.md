---
title: "Ubuntu 11.04 Live CD 'Invalid or Corrupt Kernel Image"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by Fungasaurus on 2011-06-04
First things first, i'm using Maverick Meerkat (10.10) 

I have downloaded and burnt the contents of the 11.04 ISO file onto a disc. However upon booting with it, a message appears stating 'Invalid or Corrupt Kernel Image' following with 'Boot='

It then loads the boot image and this loops. The reason why i'm trying to boot from this even though i'm using ubuntu is because I simply want to try the broadcom wireless fixes without having to upgrade. Since I would require to roll back to 10.10 to use the internet extensively. 

_Questions_

1. What should I do to fix this 'invalid or corrupt image' 

2. I have tried the broadcom wireless fixes (i'm using a broadcom wireless card 4311) and it doesn't work 100%. Are there any other methods to fix it?

---

### Post by Mariane on 2011-06-04
It could be that something went wrong during the download or burn process. I would try again to download and then burn with slow speed settings. 

Mariane

---

### Post by Fungasaurus on 2011-06-04
Thanks i'll try again. Thankfully it doesn't take too long, i'll get back to you once i've tried again.

---

### Post by westie457 on 2011-06-04
> **Fungasaurus said:**
> First things first, i'm using Maverick Meerkat (10.10) 

I have downloaded and burnt the contents of the 11.04 ISO file onto a disc. However upon booting with it, a message appears stating 'Invalid or Corrupt Kernel Image' following with 'Boot='

It then loads the boot image and this loops. The reason why i'm trying to boot from this even though i'm using ubuntu is because I simply want to try the broadcom wireless fixes without having to upgrade. Since I would require to roll back to 10.10 to use the internet extensively. 

_Questions_

1. What should I do to fix this 'invalid or corrupt image' 

2. I have tried the broadcom wireless fixes (i'm using a broadcom wireless card 4311) and it doesn't work 100%. Are there any other methods to fix it?


Hello

Answering your questions in order.

1. Either create a live USB start-up disk or re-download the ISO and burn a LiveCD at the slowest possible burn speed to eliminate errors in the burn process. If possible use a burn speed of 1x which is a byte by byte copy.

2. If memory serves me correctly the 'STA' driver worked straight out of the box on 'Maverick' with no issues. As for the fixes, the one I posted here

[http://ubuntuforums.org/showthread.php?t=1604868&page=19](http://ubuntuforums.org/showthread.php?t=1604868&page=19)

see post #188. This works as I use the same Wireless chip. 

Also on the same thread if you go to page 24 and read post #240 by 'josephmills' there is a more detailed explanation of the solution

---

### Post by Fungasaurus on 2011-06-04
Thanks Westie, i'll try that once i've got 11.04 up and running.

---

### Post by Fungasaurus on 2011-06-04
Sweetness! It worked all working fine now. The only thing is, I made a partition incase I needed to roll back to 10.10. (Stupuid since I have a live CD of 10.10) 

_Question_

1. How can I remove the old 10.10 partition and keep 11.04 intact?

---

### Post by westie457 on 2011-06-04
> **Fungasaurus said:**
> Sweetness! It worked all working fine now. The only thing is, I made a partition incase I needed to roll back to 10.10. (Stupuid since I have a live CD of 10.10) 

_Question_

1. How can I remove the old 10.10 partition and keep 11.04 intact?

Good to hear all is now okay

Now in answer to this question using my memory of something I did about 2 years ago.

I tried a LiveCD of Gparted and something went wrong. After 4 hours watching an orange bar sliding to-and-fro across the screen of the desktop PC I pulled the plug on it. That killed all info on the hard drive. _You can laugh now if you want_.

After I had re-installed everything I then tried booting into a LiveCD and ran Gparted from there. I was able to move/resize and delete and create any partition (upto 4 logical partitions) as none were mounted. Gparted does not like working on any mounted partition. 

A word of caution. Work on one partition at a time and click apply before working on the next. The whole thing took about 20 minutes.

To recap. After 4 hours of looking at nothing and 2 days of re-installing everything the quick way was to do it one step at a time.

After deleting a partition you will have to reconfigure GRUB. My suggestion for that is to go here[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

Go careful and Happy Computing

---

### Post by Fungasaurus on 2011-06-04
Well that's odd. Apparently there is no longer another partition for 10.10? Haha I guess lady luck was on my side. Thanks for your help again, I've definitely underestimated the usefulness of these forums.

---

