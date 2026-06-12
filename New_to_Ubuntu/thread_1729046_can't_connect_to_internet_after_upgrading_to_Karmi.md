---
title: "can't connect to internet after upgrading to Karmic"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by elz4 on 2011-04-14
I had been running an older version of ubuntu for quite a while with no issues, but wanted to upgrade so a currently supported version. After my first upgrade, from Jaunty to Karmic, I have had issues with both wired and wireless internet.

When I right click on the internet connections in the upper right hand corner, the "enable wireless" is grayed out.

When I tried connected with wired internet, the machine thinks for a while and then says "wired network disconnected".

I have spend a good deal of time with google, but have found nothing helpful except that this indeed was a bug in Karmic...but the pages where the bug was described seemed to have no help as to how to fix it.

Thanks in advance for any help, it would be very much appreciated!

---

### Post by fabricator4 on 2011-04-14
> **elz4 said:**
> When I tried connected with wired internet, the machine thinks for a while and then says "wired network disconnected".


I don't have a solution to your network problem, but support for Karmic stops in a few weeks as well.  I would recommend a new installation of the current Long Term Support release, 10.04 Lucid.  It will get support until April 2013, is very stable, has no network problems (that I know of) and everything pretty well works as advertised.

If you haven't already done so, I also recommend setting up a separate /home partition.  Lucid will only need 15 - 20 GB and the rest your drive can be allocated as /home (plus a swap partition of course).  This simplifies maintenance, upgrade, and repair of the / partition while protecting your data and settings from these operations.

Chris

---

### Post by elz4 on 2011-04-14
Yes I was going to immediately upgrade from Karmic, but to run the upgrade I needed to connect to the internet :/ I was trying to avoid a new installation and more partitioning because it scares me a little, so I would really like to find a way to connect to the internet (wired OR wireless) and let the update work its magic automatically!

However if partitioning is what I need to do, I will have many questions and will probably need to start a new thread if I can't find some very basic step by step instructions :o

---

### Post by fabricator4 on 2011-04-14
> **elz4 said:**
> Yes I was going to immediately upgrade from Karmic, but to run the upgrade I needed to connect to the internet :/ I was trying to avoid a new installation and more partitioning because it scares me a little, so I would really like to find a way to connect to the internet (wired OR wireless) and let the update work its magic automatically!

However if partitioning is what I need to do, I will have many questions and will probably need to start a new thread if I can't find some very basic step by step instructions :o

Yes, if you needed to upgrade to more than the next release, it's really easier to just download the LiveCD for the new release otherwise you have to upgrade each release until you get to where you need to be.  The only alternative is that you can upgrade from one LTS release to the next. LTS releases come out every two years.

There's another reason to download the LiveCD too - if you ever need to repair, re-install, or install to another machine you really need the bootable CD (or USB) to do so.

If you re-partition with a /home partition then it can make life much easier in the future.  The Ubuntu 10.04 install manual is here[https://help.ubuntu.com/10.04/installation-guide/i386/module-details.html]("https://help.ubuntu.com/10.04/installation-guide/i386/module-details.html")

When you manually partition the drive, specify 15 or 20 GB for the OS, a swap partition equal or bigger than your RAM size, and leave the rest for data.  The exact size of the / (root) partition really depends on how many extra programs you want to add to the system.  I find 15 GB plenty, and my netbook only has an 8 GB SSD drive.  Installing seems to be favourite topic around here, so google any questions you might have and ask questions if you have to.

You will of course have to back up all your data.  Really, you should have backed up before you started the upgrades.  If the upgrade had failed you wouldn't be the first person to lose access to their data and have to go about recovering it.  Normally people try this shortcut because their CD/DVD burner is broken.  Then, when they find that the OS is now broken they have absolutely nothing they can do to boot it up and get it working.  ;-)

Chris.

---

### Post by fabricator4 on 2011-04-14
When I said "leave the rest for data" I really should have said "Use the rest for the ext4 partition that you will make /home".  Wouldn't like to think you'd just leave it blank and expect the manual partition/install to find it and use it... it won't

BTW, the only hard part about doing the manual partition is making sure that the right partitions mount as '/' and '/home' - there's a drop down box for selecting this.  Make both these partitions ext4.

The only other thing is to check that Grub is being installed to /dev/sda - that's the first hard drive in the system.

Chris.

---

### Post by K_45 on 2011-04-14
> **fabricator4 said:**
> When I said "leave the rest for data" I really should have said "Use the rest for the ext4 partition that you will make /home".  Wouldn't like to think you'd just leave it blank and expect the manual partition/install to find it and use it... it won't

BTW, the only hard part about doing the manual partition is making sure that the right partitions mount as '/' and '/home' - there's a drop down box for selecting this.  Make both these partitions ext4.

The only other thing is to check that Grub is being installed to /dev/sda - that's the first hard drive in the system.

Chris.

And you'd want all three partitions as primary.

---

### Post by fabricator4 on 2011-04-15
> **K_45 said:**
> And you'd want all three partitions as primary.

Why would you want to do that?  If you use the manual partitioner in the installer and just set up three partitions it will only make the boot partition primary.  Under the hood it automatically makes an extended partition with other two partitions on it.  This is not obvious until you look at it later with Gparted or similar.

Do you have any references for why this would be desirable?

Thanks

Chris.

---

### Post by K_45 on 2011-04-15
> **fabricator4 said:**
> Why would you want to do that?  If you use the manual partitioner in the installer and just set up three partitions it will only make the boot partition primary.  Under the hood it automatically makes an extended partition with other two partitions on it.  This is not obvious until you look at it later with Gparted or similar.

Do you have any references for why this would be desirable?

Thanks

Chris.

Personal preference. I know on all my systems that sda3 is /home, sda1 is /, and sda2 is swap. So if I ever need to fiddle with the partitions, I know what's what. I don't think it makes any difference. A partition is a partition. And here:

[http://www.linuxforums.org/forum/installation/145732-logical-extended-partition-vs-primary-performance-differences.html](http://www.linuxforums.org/forum/installation/145732-logical-extended-partition-vs-primary-performance-differences.html)

---

### Post by elz4 on 2011-04-22
Thanks so much for the help. Turns out the problem was that the external wireless switch wasn't on - which I didn't think to check for since I dual boot on that machine and the wireless worked fine in windows. Man I feel dumb! But so glad the problem is fixed:D So, if anyone else is having that problem, even if the wireless is working in another OS, check that out!

So, I am just going to do the upgrade to the LTS version using the upgrader thingy, and not worry about new partitions because all this /home and /swap partitioning stuff is a little scary still. I am really an ABSOLUTE beginner! So I just make sure to keep everything backed up in case of any problems.

Thanks again for the help!

---

