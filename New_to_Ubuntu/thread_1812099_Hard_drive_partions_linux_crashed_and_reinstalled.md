---
title: "Hard drive partions linux crashed and reinstalled"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by Robr0924 on 2011-07-25
I'm running both win7 and linux on my pc.

This is what I want:

When you turn on the pc I want it to default to windows7, if no choice is made.  Currently it goes to linux is no choice is selected.

2.  I installed on saturday, and during the updates the PC was shut off.  And linux would not load.  I reinstalled and upgraded to 11.04 for 10.10.  Everything is working but the hard drive is split 4 ways to sunday.

Essentially I want the PC split 50/50 between windows and linux.  How can i accomplish this?

Complete newb here please be gentle.

Thanks 

Rob

---

### Post by bigpayne69 on 2011-07-25
Well, two things in regards to your first question. all you need to with grub is to open the grub menu file in gedit under sudo. Once you get it open, edit the menu so that the Windows entry is at the top of the list. there a lots of threads to show you the commands to open it. As for the partition issue, Windows 7 uses like 3 partitions and your Linux is using at least 2. The only ones you should adjust are the main data partitions of each OS (they should be the biggest ones).

---

### Post by amjjawad on 2011-07-26
> **Robr0924 said:**
> When you turn on the pc I want it to default to windows7, if no choice is made.  Currently it goes to linux is no choice is selected.


[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)


> Essentially I want the PC split 50/50 between windows and linux.  How can i accomplish this?


You need first to understand how Linux deals with Partitions:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

It's up to you of course to choose 50/50 between Win and Linux but just two points you must be aware of:

1- Whenever you want to resize a Windows Partition, use a Windows Tool to do this.

2- Whenever you want to resize a Linux Partition, use [GParted]("http://gparted.sourceforge.net/") to do that.

GParted can be accessed from the LiveCD of Ubuntu.

System > Administration > GParted and you need to boot "from the LiveCD" in order to resize Linux Partitions.

---

