---
title: "How to create a Ext4 and Swap partition between two NTFS partitions ?"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by stykat on 2011-03-15
Since i have my hard disk i had two partitions , first one was where i  had my Operating system ( Windows XP ) and the other is where i put all  my projects and data.
I would really like to install Ubuntu because i like to use it but i  cannot get rid of Windows XP as most of my applications are compatible  only with it (e.g. MS office that we have to learn for school or playing Ultima Online )  . 
Is there any way i could merge some space between the two partitions ( i  got enough space on my second partition and there is no OS there ) and  create an Ext4 partition and a Swap partition ?
I don't really need a /home partition , i was able to manage my files even without that, or just by saving them on the bigger NTFS partition. 
Probably the easiest way would be to buy a second hard disk only for the two operating systems and use the other for the data but if i install another Hard disk my Power Supply would malfunction due to lack of efficiency .


Thank you for your time,

Szucs Istvan

---

### Post by marshmallow1304 on 2011-03-15
The installation procedure has a partitioning step.  Another option is to boot in the "Try it" mode on the LiveCD and run System->Administration->GParted.


Edit: Oops, that's System->Administration->Partition Editor, as Paqman says below.

---

### Post by Paqman on 2011-03-15
You can use the Ubuntu LiveCD to make some room. Boot up into the LiveCD and go to System > Admin > Partition Editor. From there you can shrink down your current partitions and make some room for Ubuntu. You'll need about 10GB.

It's always a good idea to backup your data before modifying partitions, just in case.

---

### Post by Hero1969 on 2011-03-15
You can use a free partitioning tool such as [[COLOR="Purple"]Easeus[/COLOR]]("http://www.partition-tool.com/personal.htm") while still in XP.  However you do it, I would suggest rebooting into XP just to be sure everything is still working, then install Ubuntu, have fun!

---

### Post by Hedgehog1 on 2011-03-16
To give you an idea of the change dual boot makes to your hard drive, here is a 'typical' example:

Before:

[IMG]http://img842.imageshack.us/img842/2590/small09bpartitionsbefor.png[/IMG]

And after the Ubuntu dual boot install:

[IMG]http://img268.imageshack.us/img268/5948/small48gpartedview.png[/IMG]

***The Hedge***

:KS

---

