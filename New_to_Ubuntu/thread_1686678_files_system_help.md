---
title: "files system help"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by aslayer on 2011-02-12
Hey guys.. i'd really appreciate some help.. take a look at the disk usage pics i took from a screenshot.
I basically allocated a 4gb partition for root and 150 gb partition for home...   
However,  I can't seem to move anything OUTSIDE of the root folder .  It's basically full and as I try to download software I'm getting "almost full" warnings.  ...have been searching and trying for hours now and finally decided to ask for some assistance.
Please respond in complete noobie speak for me.   Seasoned in windows but just installed linux for the first time.  I know nothing about how to use alt f2   :/
thank you.
Mark

---

### Post by The Cog on 2011-02-12
I think maybe the best thing might be to use a live CD to re-size the partitions. Use the live CD and choose to "try now" rather than to install. Then go for System->Partition Editor. You will probably have to do it in three stages assuming / is before /home:
1: Reduce the size of the /home partition
2: Move the home partition up to leave a gap between / and /home
3: Increase the size of /. 10G should do nicely.

---

### Post by aslayer on 2011-02-13
That makes perfect sense and I've gotten a bit familiar with G-parted..  I'm dual booting with windows 7.. what do you think are the chances of wrecking that OS in the process?

---

### Post by The Cog on 2011-02-13
Honestly? Just a few percent, I guess. Since you are only trying to tinker with the Linux partitions, the most likely fail is that it somehow mangles the partition contents. This might also prevent grub from finding its required files adn thus prevent the machine from booting. Second most likely is user error doing something that mangles the disk, third is a software bug in gparted that scrambles things.

You really should have a backup, and any activity that changes the partition table has a potential for unwanted results.

It might be quicker simply to reinstall Ubuntu, deleting the partitions and making new ones, but you will of course lose your existing setup, and it's less interesting that resizing and moving partitions.

---

### Post by 3rdalbum on 2011-02-13
Back up ANYTHING irreplaceable BEFORE doing ANY partitioning.

Your root partition should be more like 10-20 GiB (probably no need for more than that).

---

### Post by wep940 on 2011-02-13
Something I would HIGHLY recommend as well is before you do anything, set the MBR back for Windows.  You can do this using the Windows install disk, or even easier is just to boot Windows, download the program mbrfix, unzip it, and run the program.  If you only have 1 physical disk, then the command would be mbrfix /drive 0 fixmbr
 
If everything goes ok resizing for Ubuntu, just post back and we can tell you how to recover grub so you can dual boot again.  But if there is a problem, or you loose data, etc., at least having reset the mbr first you'll still be able to boot Windows.  As was already mentioned, the resizing stands a chance of losing the grub information.  In such a case you would normally not be able to boot except from CD, but if you have restored the mbr first, you can at least boot Windows and possibly ask for help, etc..

---

### Post by aslayer on 2011-02-14
I generally welcome a healthy amount of risk and curiosity,, however i've already re-installed windows twice during my new computer build.. I would rather go a bit safer route this time if that means just a simple re-install..  how would I go about reinstalling and do I need to take the prescribed steps for managing the bootloader if I do.   Mark

---

### Post by aslayer on 2011-02-14
...just for clarity its a dual boot with win 7 occupying the first 2 primary partitions and I have a RAID 0 setup with 2 hd's.

---

### Post by wep940 on 2011-02-14
Again, mbrfix is simple, and sets the boot record so you boot Windows by default so you won't be left with a system that won't boot if you somehow damage or move grub files so they aren't found by the boot loader.  It will make your life much easier.
 
While I can't off the top of my head give you the exact command list and syntax, you can either reinstall Ubuntu, which will update your boot record, or to find an existing installation:
 
[LIST]
[*]boot from a LiveCD
[*]sudo update-grub (I really think there is something before that, but I can't remember off the top of my head)
[/LIST]

---

### Post by aslayer on 2011-03-06
I am having the hardest time using the "simple" mbrfix to restore my mbr to windows.  can someone explain step by step?  when i click on the mbrfix.exe it shows the dos prompt for 1/10 second and disappears.  I've read the user manual and can't figure out how to access the commands.  thks

---

