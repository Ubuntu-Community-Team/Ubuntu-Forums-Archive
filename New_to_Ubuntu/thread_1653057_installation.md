---
title: "installation"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by viditgoyal3009 on 2010-12-26
hello everyone,

i bought an hp dv6 3050tx laptop 2 days back and they have installed my windows on c drive and which is also the largest partition for me to store files.. i want to install ubuntu 10.10 on my laptop but since my c partition is largest i have it to install it on this drive.
will by partition get formated if i install it on this drive?? and what boot loader should i select during installation?? please reply

---

### Post by mikewhatever on 2010-12-26
Yes, the partition will get formatted, don't select it, but resize instead. W7 should have a tool for resizing its partitions. As for the bootloader, live the default settings.

---

### Post by viditgoyal3009 on 2010-12-27
whenever i try to install it, it says invalid root file system selected... what should i do??

---

### Post by Quackers on 2010-12-27
First have a look at the Windows disk management screen and see how many primary partitions are currently in use. HP have a nasty habit of using 4, which is the maximum number of partitions on any one disc.
If you have 4 primarys already, you will need to delete one before making a new extended partition, in which you can install other operating systems.
If you try to create a 5th primary partition it will cause problems!

---

### Post by viditgoyal3009 on 2010-12-27
> **Quackers said:**
> First have a look at the Windows disk management screen and see how many primary partitions are currently in use. HP have a nasty habit of using 4, which is the maximum number of partitions on any one disc.
If you have 4 primarys already, you will need to delete one before making a new extended partition, in which you can install other operating systems.
If you try to create a 5th primary partition it will cause problems!
hp had created 3 partitions, i split c drive into 3 partitions, 1st for window, 2nd for ubuntu and 3rd for storing personal files.. during drive splitting it said that the partitions created will be dynamic. i have alloted 50gb for ubuntu but that drive doesn't show up during installation.

---

### Post by Quackers on 2010-12-27
If your partitions are now dynamic you can forget about installing Ubuntu for the moment. Ubuntu won't even see your existing partition setup now. As soon as you attempted to create a 5th primary partition Windows changed the existing partitions to dynamic discs. Dynamic discs are ok for Windows, but nothing else, as far as I know. (That's probably why they do it).
You can change them back to basic partitions if you want to. Have a read of the info in this link
[http://www.dynamic-disk.com/windows-7-convert-dynamic-disk-to-basic.html](http://www.dynamic-disk.com/windows-7-convert-dynamic-disk-to-basic.html)

---

### Post by amjjawad on 2010-12-27
> **viditgoyal3009 said:**
> hello everyone,

i bought an hp dv6 3050tx laptop 2 days back and they have installed my windows on c drive and which is also the largest partition for me to store files.. i want to install ubuntu 10.10 on my laptop but since my c partition is largest i have it to install it on this drive.
will by partition get formated if i install it on this drive?? and what boot loader should i select during installation?? please reply

The[** Dual-Booting Guide**]("http://ubuntuforums.org/showthread.php?p=10257675") (check my signature) has the answers for your questions.

[COLOR=Red][B]_Edit_: Please accept my apology, I didn't read [Quackers's reply]("http://ubuntuforums.org/showpost.php?p=10283479&postcount=6").
[COLOR=Black]However, once you convert your partitions to basic, you can carry on normally.
[/COLOR]
[/B][/COLOR]

---

### Post by hello2012 on 2010-12-27
I think Quackers share the useful information to us. And I also think it can help you solve your problem.

---

### Post by viditgoyal3009 on 2010-12-29
windows 7 is not giving me the option to convert a dynamic disc to a basic disk... any other method??

---

### Post by hello2012 on 2011-01-07
[FONT=Times New Roman][SIZE=3]Windows 7 can not help you convert dynamic disk to basic disk, I found Dynamic Disk Converter, because I used to convert basic to dynamic on windows 7, through this tool, I convert it back. Take the information: [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3][COLOR=#800080]convert dynamic disk to basic windows 7[/COLOR][/SIZE][/FONT]]("http://www.dynamic-disk.com/windows-7-convert-dynamic-disk-to-basic.html")[SIZE=3][FONT=Times New Roman].[/FONT][/SIZE]

---

