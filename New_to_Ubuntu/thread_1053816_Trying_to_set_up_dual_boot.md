---
title: "Trying to set up dual boot"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by jaqrah on 2009-01-29
Hi.  I am trying to set up my desktop to dualboot Xp & Ubuntu.  I have read various how to guides and thought I was good to go.  But I got to step 4 of 7, Prepare disk space, and I am stuck.  Most of the tutorials say that I can resize my xp partition to make space for Ubuntu.  Except, despite my choices to partition, my choices only leave me with using the whole drive for ubuntu.  What have I done wrong or am I missing something?  Any help would be greatly appreciated.

Jaq

---

### Post by Elfy on 2009-01-29
Make sure to defrag a couple of times, you might also find that you need to turn of the pagefile and possibly hibernate if you use it.

---

### Post by Boomhauer on 2009-01-29
if you are still in the install process, you can click cancel to get to the ubuntu live desktop.  if you are no longer in the install process, boot the ubuntu cd and then choose 'try ubuntu without installing'  
either way you will end up at the live desktop.  now you need to go to System>Administration>Partition Editor.  that will launch a program that which will let you shrink your vista partition and create one for ubuntu.  as forestpixie suggested you will want to defrag vista before you do this.

---

### Post by jaqrah on 2009-01-29
Thanks ...I did defrag and I have 30 gigs free.  

I ventured into the manual setup.  I have three partitions:

/dev/sda1  fat 16
/dev/sda2  ntfs    (this partition has the 30gb of free space)
/dev/sda3  fat 32

I am presuming I need to edit the partition for sda2...but how do I set that up?

---

### Post by Boomhauer on 2009-01-29
if you do what i said in post 3 to start, then when you are presented your partitions, you can double click sda2.  that will bring up another window and in that window, you can click and drag the right edge of the partition to the left to create new space. you could create 10-15GB partition for ubuntu and then it would leave you space for stuff that you might want to install in windows in the future.  its up to you really. after you do that youll need to click apply.  once you get your partitions set up, and you are installing ubuntu, select manual as you have previously done and then double click the new partition in the list that you have created.  you will want to format it to ext3 and for the box that says mountpoint, choose /  after this you can click next to continue installing to your new partition.  be careful here, you dont want to overwrite windows.

---

### Post by Elfy on 2009-01-29
You need to create an extended partition so that you can have a / and a swap - or make no partitions just create the free space and then tell the installer to use the free space.

Make sure you have backups of any data you can't afford to lose when playing with partitions.

---

### Post by jaqrah on 2009-01-29
Boomhauer...thanks for advice.  I did what you said and discovered I had a bad sector.  It is why I couldn't resize.  I am following the screen suggested remedies and will try to resize after that.

Forest Pixie...thanks for your help as well.

---

