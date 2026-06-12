---
title: "Help! New user  hp 210 2 probs"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by hendryjosh@gmail.com on 2011-01-22
First off I love the program! I have been a long time mac user but recently bought an hp mini 210-2000. I had planned on running windows 7 and ubuntu side by side. I partitioned half the drive in windows (ended up with over 100gb for each system) Did the usb install- choose to install in the partition that i made and boot at \. Ubuntu starts and works great! 
Problem #1 is I cant use wireless. I read in some threads to connect to ethernet and update
(this computer has no ethernet plug). Can I download a magic driver onto a usb with another computer and load onto the mini to fix that prob?

Prob#2 I get no option to boot into windows. What did i do wrong and how can I fix it? I have a few programs that require windows or mac is the only reason i want to keep it!

Thanks for any help! Easy steps please!

---

### Post by Quackers on 2011-01-22
Welcome to UF.
For problem 2 open a terminal and run ```
sudo update-grub
```
and watch as grub.cfg is run, to see if the Windows Loader is picked up. If it is, reboot and try to boot Windows from the grub menu.
Sorry, don't know about problem 1.

---

### Post by Jerry N on 2011-01-22
I have a Mini 210-1180 and it has an ethernet connector.  It is on the right side, near the back, right between a USB connector and the lock symbol.  There is a black plastic cover over the ethernet connector.

How did you partition your hard drive?  Did you have to delete an existing partition? My Mini 210 has all 4 partitions used and I was considering deleting the HP Tools partition.

Jerry

---

### Post by hendryjosh@gmail.com on 2011-01-22
> **Quackers said:**
> Welcome to UF.
For problem 2 open a terminal and run ```
sudo update-grub
```
and watch as grub.cfg is run, to see if the Windows Loader is picked up. If it is, reboot and try to boot Windows from the grub menu.
Sorry, don't know about problem 1.

I tried it and saw no windows loader-

---

### Post by hendryjosh@gmail.com on 2011-01-22
> **Jerry N said:**
> I have a Mini 210-1180 and it has an ethernet connector.  It is on the right side, near the back, right between a USB connector and the lock symbol.  There is a black plastic cover over the ethernet connector.

How did you partition your hard drive?  Did you have to delete an existing partition? My Mini 210 has all 4 partitions used and I was considering deleting the HP Tools partition.

Jerry
Wow thanks Jerry I can't believe I missed that! That will teach me to not have coffee! As for the partition I didnt have to delete anything I just used half of C: here is the directions I followed
[http://techpp.com/2010/01/19/how-to-partition-a-hdd-hard-disk-in-windows-7/](http://techpp.com/2010/01/19/how-to-partition-a-hdd-hard-disk-in-windows-7/)
thanks - josh

---

### Post by Quackers on 2011-01-22
That could be a problem. Have a look in the disk management screen in Windows, or gparted in Ubuntu. How many primary partitions are in use?

---

### Post by Jerry N on 2011-01-22
I looked at the linked instructions and they appear to be starting with a computer having only 3 of the 4 allowable primary partitions.  My Mini 210 shows that 4 are being used:  199mb NTFS system partition (don't mess with that one), 218GB NTFS C: drive (that is the one you shrunk to make more space), 14GB NTFS D: drive (Recovery Drive) and 103 MB Fat32 E: drive (Hp tools partition).  The recovery drive has all the stuff necessary to return the computer to its factory state.  I don't know why HP started using a partition for their tools - that stuff used to be on the C: drive.  Using gparted in Ubuntu, what do your partitions look like now?

Jerry

---

### Post by hendryjosh@gmail.com on 2011-01-22
> **Quackers said:**
> That could be a problem. Have a look in the disk management screen in Windows, or gparted in Ubuntu. How many primary partitions are in use?

Not to sound extremely dumb, but where do I find gparted?

---

### Post by Quackers on 2011-01-22
Connect an ethernet cable and run System > Admin > Hardware Drivers (or Additional Drivers). This may give you a driver for the wireless card.
You will need to install gparted if you haven't done that already. Go to System > Admin > synaptic package manager and when the window opens enter "gparted" in the search box. When it appears in the main window right-click on it and select "mark for installation". Then click on the green arrow in the toolbar to apply the change. When installed go to System > Admin > gparted.

---

### Post by Jerry N on 2011-01-23
> **hendryjosh@gmail.com said:**
> Not to sound extremely dumb, but where do I find gparted?

Not a dumb question!  gparted is not a part of the installed Ubuntu but Quackers has explained how to install it.  gparted is a Linux partition manager and why it isn't pre-installed in Ubuntu I have no idea.  You saw it during your Ubuntu install but it takes a few installs to really grasp it.  

Jerry

Correction - you would see gparted during installation only if you select manual install.  I always use manual partitioning on Linux installs.  go to [http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)  to see a gparted screen.

---

### Post by hendryjosh@gmail.com on 2011-01-23
> **Quackers said:**
> Connect an ethernet cable and run System > Admin > Hardware Drivers (or Additional Drivers). This may give you a driver for the wireless card.
You will need to install gparted if you haven't done that already. Go to System > Admin > synaptic package manager and when the window opens enter "gparted" in the search box. When it appears in the main window right-click on it and select "mark for installation". Then click on the green arrow in the toolbar to apply the change. When installed go to System > Admin > gparted.

Thanks for the directions. If i'm interpreting it correct (doesnt happen very often) The only thing now on my computer is Ubuntu!
It only shows my hard drive 232.88 gib 6.27 gib used. I think I messed up!

---

### Post by hendryjosh@gmail.com on 2011-01-23
Problem number 1 is solved! Thanks to Jerry for pointing me to the hidden ethernet plug! After a system update it worked perfect. If I would have selected Install updated during the install im assuming that would have worked fine!
Now to focus on problem #2 the lack of windows7 (which could be seen as a good thing):)
Thanks for the help so far Jerry and Quackers!

---

### Post by Jerry N on 2011-01-23
> **hendryjosh@gmail.com said:**
> Thanks for the directions. If i'm interpreting it correct (doesnt happen very often) The only thing now on my computer is Ubuntu!
It only shows my hard drive 232.88 gib 6.27 gib used. I think I messed up!

Are you saying that you only see one partition, like /dev/sda1, and it has a size of 232gb?  If so, you truly wiped out Win 7 and the recovery partition.  If you really want Win 7 back, and you have wiped out the recovery partition, you might be able to buy a recovery disk set from HP.  The last time I had to do that for someone the cost was about $15.  Of course you would need a USB connected DVD reader.

I bought my Mini 210 because it was much smaller and easier to carry on a trip than my 5-6 year old laptop.  I have found that smaller is its ONLY virtue.  I upped the RAM to 2 gb but the CPU is the primary performance constraint, not the RAM.  And I know it wouldn't fit in the case but I miss the CD/DVD capability.  Knowing what I know now, I wouldn't buy another one.  

Jerry

---

### Post by hendryjosh@gmail.com on 2011-01-24
[QUOTE=Jerry N;10390434]Are you saying that you only see one partition, like /dev/sda1, and it has a size of 232gb?  If so, you truly wiped out Win 7 and the recovery partition.  If you really want Win 7 back, and you have wiped out the recovery partition, you might be able to buy a recovery disk set from HP.  The last time I had to do that for someone the cost was about $15.  Of course you would need a USB connected DVD reader.

I bought my Mini 210 because it was much smaller and easier to carry on a trip than my 5-6 year old laptop.  I have found that smaller is its ONLY virtue.  I upped the RAM to 2 gb but the CPU is the primary performance constraint, not the RAM.  And I know it wouldn't fit in the case but I miss the CD/DVD capability.  Knowing what I know now, I wouldn't buy another one.- Jerry 

I also bought mine for the portability. I have an ibook g4 that is a 2005 and still works fine! As far as the 210, for 300 and change I didnt expect a top performer! It will do for what I need, I also get to learn a new OS! Thanks for everything, the support for this program is GREAT- Josh

---

### Post by hendryjosh@gmail.com on 2011-01-25
> **Jerry N said:**
> Are you saying that you only see one partition, like /dev/sda1, and it has a size of 232gb?  If so, you truly wiped out Win 7 and the recovery partition.  If you really want Win 7 back, and you have wiped out the recovery partition, you might be able to buy a recovery disk set from HP.  The last time I had to do that for someone the cost was about $15.  Of course you would need a USB connected DVD reader.

I bought my Mini 210 because it was much smaller and easier to carry on a trip than my 5-6 year old laptop.  I have found that smaller is its ONLY virtue.  I upped the RAM to 2 gb but the CPU is the primary performance constraint, not the RAM.  And I know it wouldn't fit in the case but I miss the CD/DVD capability.  Knowing what I know now, I wouldn't buy another one.  

Jerry

Jerry In case you are curious- when I made the new partition and attempted to manually install ubuntu it did in fact totally wipe everything clean. I contacted hp and can get 7 on a thumb drive for 20 bucks, but i think ill just stick with ubuntu! Thanks for all the help!

---

