---
title: "s:grub&gt;"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by azekee on 2010-09-12
Hello! 

GRUN GRUB version 1.97-beta 4

s:grub>


Can someone help me please !  
I have istalled Ubuntu 9.10 desktop edition,and I am running dual boot with Windows 7 
After playing around ,I can't no longer boot neither in Ubuntu 9.10 or Windows 7. unfortunatly I don't have Windows 7 cd so I can't fix from there.
I do have Ubuntu 9.10 live CD.
I am totally lost and have no idea what to Do :(

My partitions now look like this 

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        4809    38520724    7  HPFS/NTFS
/dev/sda3            5597        9729    33198322+   5  Extended
/dev/sda5            5597        6183     4702566   83  Linux
/dev/sda6            6184        7004     6594651   83  Linux
/dev/sda7            7005        7048      353398+  82  Linux swap / Solaris
/dev/sda8            7049        7119      563200   82  Linux swap / Solaris
/dev/sda9            7120        9615    20049088+  83  Linux
/dev/sda10           9616        9729      915673+  82  Linux swap / Solaris

Can someone help me please to fix this problem ?

Thank you in Advance !

---

### Post by coffeecat on 2010-09-12
You have three Linux partitions and three Linux swap partitions! Did your "playing around" involve re-installing Ubuntu a further two times?

Something has clearly gone wrong with the grub installation and it can't find its configuration files on whichever of the three root partitions it would be - I think the poor thing has got lost. Normally, it would be easy to repair grub and get you booting again, but without knowing which of those three partitions grub should be pointing to, that's going to be difficult. Besides, your Linux partitions are in such a mess, using up space unnecessarily, that it might be better to wipe them all out and reinstall Ubuntu yet again - this time to the requisite number of partitions. If you do that, grub should pick up Windows and get you back to dual-booting again.

Before telling you how to do this, a few questions:

Is that what you want to do?

What was the nature of the 'playing around'?

Were you successfully dual-booting before the 'playing around'?

Why did you need to play around? Was there a problem you were trying to fix?

By the way, you posted the output of 'sudo fdisk -l' but you omitted the first bit. Which means I can't calculate all those partition sizes, which would be a good idea  before advising you further.

---

### Post by azekee on 2010-09-13
Hello coffeecat,
I have wiped them all out and installed Ubuntu 10.04 and  deleted windows 7,and I am very happy man right now for a good advise you have gave me . Everything runs smoothly .
And just to answer your quest. 1)I was trying to install a program (backtrack). 2) I was  successfully dual-booting before the 'playing around' 3)I have that need to play around with things ,and there were no problem I was trying to fix . Now then everything is sorted I am thinking to open my laptop to see what is inside:)

Thank you coffeecat for finding time to help me . God bless !  Take care !

---

