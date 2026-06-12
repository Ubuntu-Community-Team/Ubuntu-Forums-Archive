---
title: "Adding windows to an ubuntu machine"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by newport_j on 2010-07-19
I have a lap top with only Ubuntu 8.04 on it. I want to add Windows XP. I want to make it a dual boot machine. What is the procecdure for this? I do not want to destroy my version of Ubuntu 8.04 that is on the machine at present.
 
Newport_j

---

### Post by Jazzy_Jeff on 2010-07-19
What do you need Windows for? If you are not doing anything that requires high graphics I would just install Virtual Box and install Windows through it.

---

### Post by tarps87 on 2010-07-19
Basically use the Ubuntu live disk to repartition the hard drive, make a note of the sizes and tell the windows installer to use the partition which is empty (you'll have to tell windows this, it won't work it out itself).
You will then need to repair the MBR, this should help with that:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Don't forget to backup all important data.

---

### Post by byStanderone on 2010-07-19
...installing windows after ubuntu, will wipe the mbr in the ubuntu partition. before doing what you intend to do, would suggest you first go thru the threads on re-installing mbr after a windows install. there are lots of threads in the forum about this subject.

---

### Post by skarme on 2010-07-19
> **newport_j said:**
> I have a lap top with only Ubuntu 8.04 on it. I want to add Windows XP. I want to make it a dual boot machine. What is the procecdure for this? I do not want to destroy my version of Ubuntu 8.04 that is on the machine at present.
 
Newport_j
You'll have to install Windows on a new partition. If a partition isn't created, you may do so using GPARTED. It will let you create a new partition without erasing Ubuntu 8.04 (but taking a backup of important data is always advisable).
Once this is sorted out, you may install Windows and specify the partition to install in during setup.
Windows will erase GRUB.
As a result of this your PC will boot straight into Windows.
To restore GRUB you may use your Ubuntu Live CD.
Now you have a dual boot PC.

---

### Post by newport_j on 2010-07-19
Ok, here is the deal. My wife is taking a computer graphics course that started last month. It will last all summer, the text comes with the CD's of Adobe Illustrator and Adobe Photshop. They are not set up to last indefinitely. They will last only 30 days each, from the date they were installed. The first part of the course used Adobe Illustrator. that part just ended. The second aprt of the course uses Adobe Photoshop and that part is begining now. 
 
We installed both Illustrator and Photoshop at the start of the course. Now I want to use Photoshop and the 30 days has expired. So I must put it on a new computer. I have a Ubuntu computer and a Windows XP disk. So I will install windows there and remove from my first computer. That violates no copyright laws. 
 
Yes, I know I should have waited until the last half of the course to install Photshop, but I did not. I do not believe that I am the only one with this issue in the course. As I said my wife is takng the course, she is a good artist but not that sophistitcated with a computer and these types of installations.
 
So I want to install Window XP on a computer that already has Ubuntu on it. At the end of the sumer, I will reverse the above action and have, hopefully, an Ubuntu only laptop and a Windows only Desktop. 
 
For now I just want to install Windows on my laptop which has Ubuntu only on it now. That will make it a dual boot computer. Now is there a website thta has a detailed decrition of how to do it? If so where?
 
I installed Ubuntu on a Windows only computer once with no problem. How do I do it the other way around?
 
 
Newport_j

---

### Post by skarme on 2010-07-21
> **newport_j said:**
> Ok, here is the deal. My wife is taking a computer graphics course that started last month. It will last all summer, the text comes with the CD's of Adobe Illustrator and Adobe Photshop. They are not set up to last indefinitely. They will last only 30 days each, from the date they were installed. The first part of the course used Adobe Illustrator. that part just ended. The second aprt of the course uses Adobe Photoshop and that part is begining now. 
 
We installed both Illustrator and Photoshop at the start of the course. Now I want to use Photoshop and the 30 days has expired. So I must put it on a new computer. I have a Ubuntu computer and a Windows XP disk. So I will install windows there and remove from my first computer. That violates no copyright laws. 
 
Yes, I know I should have waited until the last half of the course to install Photshop, but I did not. I do not believe that I am the only one with this issue in the course. As I said my wife is takng the course, she is a good artist but not that sophistitcated with a computer and these types of installations.
 
So I want to install Window XP on a computer that already has Ubuntu on it. At the end of the sumer, I will reverse the above action and have, hopefully, an Ubuntu only laptop and a Windows only Desktop. 
 
For now I just want to install Windows on my laptop which has Ubuntu only on it now. That will make it a dual boot computer. Now is there a website thta has a detailed decrition of how to do it? If so where?
 
I installed Ubuntu on a Windows only computer once with no problem. How do I do it the other way around?
 
 
Newport_j
You need to install GRUB after installing windows to make a dual boot PC.
This link has details on how to install GRUB. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Once you are done installing Windows, refer to the above link to install GRUB.

---

