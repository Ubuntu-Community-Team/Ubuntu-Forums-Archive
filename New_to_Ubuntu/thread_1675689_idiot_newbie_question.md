---
title: "idiot newbie question"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by seanypoo26 on 2011-01-26
Okay, I got to be quite an expert at windows but it finally crapped out and I switched to Ubuntu.  Love it but I have a dumb question.  I used to have 3 hard drives when I used windows but now I dont know how to access the other 2!  Where are they?  My primary says it is almost full but I have another 160 gb and a 250gb.  What am i supposed to do?
Sorry for being such an idiot!

---

### Post by pbpersson on 2011-01-26
1.  In order to see if Ubuntu recognizes all the hard drives in your system, run GPartEd and see if you can see all the hard drives and partitions.  It is in system-->administration

2.  To mount the additional hard drives in a folder, follow these instructions:  [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

Hint:  It is simpler if you create the folders in your home folder, especially if you are the only user of the computer.

---

### Post by Quackers on 2011-01-26
Welcome to Ubuntu and UF :-)
Do the other drives show up in Places menu?

---

### Post by ruegore on 2011-01-26
Click on Places, then Computer.
You should see your drives there. They are usually not mounted. Just double-click them to automagically mount the drive and from there you should easily navigate wherever you want to.

You could optionally edit your fstab file to mount these drives automatically everytime you boot into Ubuntu.

---

