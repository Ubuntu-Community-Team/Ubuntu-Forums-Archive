---
title: "Creating a dual booot / partition with Wubi ?"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by smuir00 on 2009-02-07
Hi, I have just downloaded ubuntu 8.10 and am trying to create a partition in my windows vista PC so that when I boot up I can choose to load windows vista or Ubuntu.  When I boot up with the CD in the drive it does not give me an option to create ubuntu within windows ? The options include: install or run from disk (which seems to take ages, has the logo on the screen but nothing seems to happen ?).

Help, what option should I choose to create the partition and load ubuntu ?

Any help appreciated

Simon

---

### Post by KuroYoma on 2009-02-07
Hello Simon,

Did you download an ISO file and then burn it to a cd/dvd for your ubuntu 8.10 or did you order one online.  If you burnt it yourself can you download Daemon Tools and mount the original ISO file and see if it gives you the Wubi option then.

---

### Post by Hendrixski on 2009-02-07
I've not used Wubi yet, I've heard good things, but I'm a fan of install by disk.  If you can, just download the .iso file from ubuntu.com,  burn it to disk (which requires a disk-burning utility, in Windows because it's an "image" and MS can't figure out how to get that to work) pop it into your cd-drive and boot up.  The installer is easy as pie.

---

### Post by talsemgeest on 2009-02-07
> **smuir00 said:**
> Hi, I have just downloaded ubuntu 8.10 and am trying to create a partition in my windows vista PC so that when I boot up I can choose to load windows vista or Ubuntu.  When I boot up with the CD in the drive it does not give me an option to create ubuntu within windows ? The options include: install or run from disk (which seems to take ages, has the logo on the screen but nothing seems to happen ?).

Help, what option should I choose to create the partition and load ubuntu ?

Any help appreciated

Simon
Since you have already burned the iso to a disc, it is relatively simple to install inside windows. You simply have to run the cd (from "My Computer"), and choose "Install inside Windows." This will bring up the wubi installer, which will ask you some questions, then install Ubuntu onto a file inside windows. Once it is finished, you can start into ubuntu by restarting your computer and choosing Ubuntu.

---

### Post by nhasian on 2009-02-07
smuir00,

To resize a partition with Windows Vista, follow these steps:

Be sure to back up any valuable information, because there is a slight chance that data can be lost when dealing with partitions.

1) Click on the Start menu

2) Right click on Computer and click on Manage

3) You may get a User Account Control dialog here; just click Continue

4) In the left pane, open up the Storage category and click on Disk Management

5) Here, you will find your partitions for your disks. Right click on the partition you’d like to modify.

6) Click on Shrink Volume to shrink the selected partition.

now you can boot off the ubuntu CD and install to the unused hard disk space.

---

