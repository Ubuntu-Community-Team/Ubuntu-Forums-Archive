---
title: "Partition, Lost Hard Disc space at instalation"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Simon Bristow on 2009-01-29
When instaling Ubuntu 8.10 I got as far as the screen where you enter name, password etc. I then clicked the 'Back' button by mistake. This returned me to the 'Prepare Disc Space' screen. The partitions now showed one with windows and about 5Mb space and another, new partition, about 5Mb which I could not access. At this point I aborted the instalation.

Windows now shows my available disc space about 5Mb lees than before. However another tool shows all my original hard disc available.

I am using windows XP with SP3.

Really looking forward to using Ubuntu but now unsure where to go next. Please keep advice in straightforward terms, I am not an experienced user.

Simon

---

### Post by taurus on 2009-01-29
Boot from Ubuntu LiveCD.  Then open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number 1.

p.s.  When you first tried to install Ubuntu, what did you do when you got to the partition screen?

---

### Post by Simon Bristow on 2009-01-29
First what is a terminal? Please excuse my ignorance but I am a beginner.

When first installing, I used guided, resize 'C' drive.

Thanks

---

### Post by Idaho Dan on 2009-01-29
Simon,
taurus is asking you to click on Applications, then click on Accessories, then click on Terminal. 
In the Terminal box type sudo fdisk -l, and hit enter.

Dan.

---

