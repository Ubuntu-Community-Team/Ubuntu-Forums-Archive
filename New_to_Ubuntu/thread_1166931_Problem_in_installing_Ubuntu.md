---
title: "Problem in installing Ubuntu"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-05-22
[COLOR="DarkOrange"][SIZE="7"]Hello, upto now I faced many problems trying to install Ubuntu but I still want to install it now I'me facing the following problem in installation [/SIZE][/COLOR]
[IMG]http://img132.imageshack.us/img132/4771/screenshots.png[/IMG]
[SIZE="6"][COLOR="DarkOrange"]I only get two options to installing Ubuntu I don't get the option for double booting I opened Partition edittor and it shows that there is a problem with my Hard Disk.[/COLOR][/SIZE]
[IMG]http://img245.imageshack.us/img245/2180/screenshot1w.png[/IMG]

---

### Post by Sef on 2009-05-22
To dual boot, you need to manual parition.  It is not hard to manually parition, but it can be confusing the first time.

---

### Post by mosaabJ on 2009-05-22
How do you manual partition

---

### Post by mosaabJ on 2009-05-22
Hello, I just want to ask as you told me if you want to dual boot you have to manual partition How can you do that and does have effect on the data that is in my hard disk

---

### Post by wpshooter on 2009-05-22
> **mosaabJ said:**
> How do you manual partition

The first thing I would do is to go back into XP and do at least 2 runs of scandisk and defrag on the XP windows O/S.

Then I would go back to your GPARTED Ubuntu parition manager and resize the XP partition, so that you have room for your Ubuntu partitions.

Then when you get into the partitioning section of Ubuntu just choose the MANUAL button which you have shown on your screen shot.  Then create 3 partitions for Ubuntu.  Create a primary / parititon for the root of your Ubuntu O/S, then create a logical /home parition for your personal use under Ubuntu and then create a logical /swap partition for use if Ubuntu would perhaps run out of physical memory.

P.S. - Just make sure that when you are doing the manual partitioning that your do not do anything (including formatting) your XP partition.

Good luck.

---

### Post by Sef on 2009-05-22
> Hello, I just want to ask as you told me if you want to dual boot you have to manual partition How can you do that and does have effect on the data that is in my hard disk


Do you have a separate home partition? If so, you will be able to save your data.  If not, then it will be overwritten.  In either case, **back up **your **data**.

wpshooter describes how to manually partition.  If you need a more basic explanation, let me know.

---

### Post by trivialpackets on 2009-05-22
Backup your data is my first recommendation.  Your data could potentially be safe the way it is, and dual-booting should not cause data loss.  With that said, I would still back up your data.  I don't have screenshots, but a walkthrough on dualbooting for 8.04 is available [here]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm").  

It's a little different in jaunty, so you may want to watch a youtube presentation of the process in jaunty, for that you could go [here]("http://www.youtube.com/watch?v=5-EgkrOBRVQ").  Best of luck!  Personally, I wiped the drive and I run xp for the limited uses I need via virtualbox, but that's not for everyone.

---

### Post by mosaabJ on 2009-05-22
Hello, I am a real beginner and it would much apreciated if you provide me with a basic explanation

---

### Post by Sef on 2009-05-22
Before attempting the install, have you done the following:

1) Have you defragged your Windows?   This should be done 2-3 times right before installing Ubuntu.

2) Have you run the Live CD for a while to make sure that your hardware is compatible with GNU/Linux?  (Settings will be lost after exiting the Live CD.)

3) Have you **backed up** your **data**?  Your data should not be lost, but there are no 100% guarantees that all will go well.

---

