---
title: "About partition problem"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by xavierkang on 2010-12-05
Question
1)Can anyone teach me how to shrink volume ?
2)When installing ubuntu want to edit partition then just install ubuntu.But after i edit my HDD to two partition,then press install now, it fail. Saying no root system or system file.I forget what it wrote already.

Teach me pls,I really a new guy for Ubuntu.

---

### Post by drpjkurian on 2010-12-05
Hi you can see the tutorials mentioned in this [link]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Devon Fletcher on 2011-01-06
**[FONT=&quot]Re: No root file system is defined -What is the workaround[/FONT]**[FONT=&quot] [/FONT]
  [CENTER][CENTER][FONT=&quot]    [/FONT][/CENTER][/CENTER]
  [FONT=&quot]1. boot Ubuntu from CD (or USB stick)
2. run Gparted (System>Administration>Partition Editor), to set up the Ubuntu Partition. I formatted the partition as ext4, this may not be essential.
3. run Disk Utility, select the partition (click on the appropriate rectangle in 'Volumes').
4. click 'Edit Filesystem Label' and type "/" (without quotes) in the 'Choose a new filesystem label' dialogue box. click 'Apply'.
5 double-click the 
&#8216;Install Ubuntu' icon, away she goes![/FONT]

---

