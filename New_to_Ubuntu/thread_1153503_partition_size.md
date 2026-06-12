---
title: "partition size"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by shadowlands on 2009-05-08
I am using the disk and it is asking me about the partition size?  How do I select the size? Do i use the Guided- resiscsl1 (0,0,0), ....

or do I select guided- use entire disk.

---

### Post by kansasnoob on 2009-05-08
This is not an easy question to answer so give me a minute to dig up some info!

---

### Post by shadowlands on 2009-05-08
Thanks.  I was told their were errors on the partitions what is a mount point and what should it be.
 > **kansasnoob said:**
> This is not an easy question to answer so give me a minute to dig up some info!

---

### Post by Didius Falco on 2009-05-08
n/m

---

### Post by presence1960 on 2009-05-08
> **shadowlands said:**
> I am using the disk and it is asking me about the partition size?  How do I select the size? Do i use the Guided- resiscsl1 (0,0,0), ....

or do I select guided- use entire disk.

If you choose "use entire disk" all of your data, partitions etc will be overwritten and Ubuntu will be written to your hard disk and the entire drive will be Ubuntu. You can use "Guided resize" or "manual" unless you want to wipe everything and just have Ubuntu.

why don't you take a look at this before proceeding that way you won't be sorry later: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

**And back up all your data first and if you are using windows and want to keep it for a dual boot set up defrag windows at least one time.**

---

### Post by presence1960 on 2009-05-08
Better yet why don't you tell us exactly what you want to accomplish, i.e. get rid of windows, dual boot windows and ubuntu , etc. Then the community can better help you achieve what you want to accomplish.

---

### Post by shadowlands on 2009-05-08
I think I only need one system.  Why would I want to seperate the partitions?> **presence1960 said:**
> If you choose "use entire disk" all of your data, partitions etc will be overwritten and Ubuntu will be written to your hard disk and the entire drive will be Ubuntu. You can use "Guided resize" or "manual" unless you want to wipe everything and just have Ubuntu.

why don't you take a look at this before proceeding that way you won't be sorry later: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

**And back up all your data first and if you are using windows and want to keep it for a dual boot set up defrag windows at least one time.**

---

### Post by kansasnoob on 2009-05-08
Beginning with 8.10 (aka: Intrepid) some of the graphics began to change in the installation GUI!

This reflects 8.04:

[http://mywebsite.bigpond.net.au/dfelderh/p24.html](http://mywebsite.bigpond.net.au/dfelderh/p24.html)

This reflects 9.04:

[http://mywebsite.bigpond.net.au/dfelderh/p22.html](http://mywebsite.bigpond.net.au/dfelderh/p22.html)

There are some huge changes in the GUI!

And then there's this from the release notes:

> Wrong display when installing to largest continuous free space on disk

When both the "Install them side by side" and the "Use the largest continuous free space" options are present, the "Use the largest continuous free space" option will display the wrong information in the partition bar that shows what the disk will look like after installation. However, selecting this option will correctly install Ubuntu into the largest empty partition. (364181) 

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

So, it's very important to know what your intention is! Do you want to dual boot? Or do you want to give it all to Ubuntu?

At this point, if you want to dual boot, I'd only use manual partitioning by first creating partitions using Gparted and then assigning the designation of those partitions using "manual" from the installation dialogue!

Clear as mud :confused:

---

### Post by shadowlands on 2009-05-08
I do not think I will need more than one system.  I need certain things to work but I can do that in wine. Correct?

---

### Post by kansasnoob on 2009-05-08
> **shadowlands said:**
> I think I only need one system.  Why would I want to seperate the partitions?

If you're sure you know you want to do that just choose "Use the entire disc", but that means you'll lose any and all data stored on the hard rive!

---

### Post by presence1960 on 2009-05-08
> **shadowlands said:**
> I think I only need one system.  Why would I want to seperate the partitions?

If you only want one OS then back up any data you want to an external media. A lot of people like a separate home partition for their data. But it is not a must. If you want to keep it simple boot the Ubuntu Live CD and at the partitioner screen choose "use entire disk" and that is exactly what will happen. Your whole disk will be Ubuntu and it's filesystem.

---

### Post by kansasnoob on 2009-05-08
> **shadowlands said:**
> I do not think I will need more than one system.  I need certain things to work but I can do that in wine. Correct?

Some things work in Wine!

---

### Post by logos34 on 2009-05-08
> **shadowlands said:**
>  I need certain things to work but I can do that in wine. Correct?

Yes. With some exceptions, you can run most windows apps on wine tolerably well

you can check [here]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")--the list is fairly extensive

---

### Post by powel212 on 2009-05-08
1.) Many things will run in Wine but you can also install Sun VirtualBox in Ubuntu and within the virtual box you can install a full version of win. Then you can really do anything. And never have to reboot.

2.)My favourite way to do an initial install with 2 or more partitions is to boot from the live cd and open the partition editor, then set my partitions, eg. shrink win partition and then in the empty space just leave it unformatted. In this way when you run the installation and you come to the partitioning section you can choose, "Use largest continuous free space", Then Ubuntu will be installed into the space we left empty when we were in the partitioner earlier. *Note: 10Gigs is enopugh for ubuntu, 20Gigs is better, but 100Gigs really gives you a lot of playing room for vitrual boxes and the like.*

Does that make sense.

I hope that helps.

Powel

---

### Post by nealaustin on 2009-05-09
Here is what I did. I installed a dual boot system. This left me an "out" Windows = 30 Gb and the rest for Ubuntu. For the first year I would occasionally use Windows. Now I haven't used it for at least a couple of months. I used the grub editor to set the wait time in Grub to 2 seconds. Before you do anything please make a recovery disk in Windows. 
Neal

---

### Post by shadowlands on 2009-05-09
everthing important saved else where

---

### Post by shadowlands on 2009-05-28
Thanks for your help!!

---

