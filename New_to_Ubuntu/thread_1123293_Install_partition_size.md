---
title: "Install partition size"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by Halddd on 2009-04-12
I bought the boxed dvd desktop version and am trying it again
I have not completed installation. The Ubuntu guided installer wants 86% of my disk space (430 MB)

Surely there is some easy way of reducing Ubuntu's space demands???

My desktop is: 2 Duo CPU E7200 @ 2.53GHz
Ram 4.00 GB
Windows Vista

---

### Post by Xender1 on 2009-04-12
the manual install option should allow you to drag the partitions to choose how big you want your ubuntu install

---

### Post by Skrynesaver on 2009-04-12
How can you have Vista on a 430 MB drive?

Ubuntu requires~2G for a base install with Gnome and all the trimmings, with just a server install it needs ~500MB

Could you check your figures and get back on this?

---

### Post by cotcot on 2009-04-12
Looking at the computers specs it is a new computer. So I guess the 430 MB is a typo and we should read 430 GB.
The installer uses all free space (or space that can be freed easily)  unless you tell it not to do so. This is possible in the manual mode as written in an earlier post or in Guided mode and resize the partitions.

---

### Post by zvacet on 2009-04-12
@ **Halddd**

Look [here]("http://psychocats.s465.sureserver.com/ubuntu/dualboot") and you will find out all possible ways to install Ubuntu.You can choose between:

1.Guided-resize to resize existing Vista partition and after that
2.Guided-use the largest continuous free space
3.Manual

I think manual option is better because that way you can install home on it´s own partition.

---

### Post by Paqman on 2009-04-12
The other really easy option is to install using Wubi, where you can specify how much space you want to give Ubuntu from a simple drop-down box on the installer. No partitioning required.

To run the Wubi installer just boot into Windows, put your Ubuntu disk in the drive, and pick "install from within Windows" from the options. It's a ridiculously easy way to get Ubuntu onto your machine.

---

### Post by Halddd on 2009-04-12
My disk is 504 GB. Ubuntu wanted 430 Gb's. 
I'll try some of the suggestions later today. 
Thanks.

---

