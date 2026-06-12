---
title: "General questions about switching to ubuntu..."
date: 2011-07-31
forum: New to Ubuntu
---

### Post by B-2-10 on 2011-07-31
I've been playing around with ubuntu for about a week, and want to make it my main OS. I think I'm right in thinking that I should uninstall my wubi installation and install ubuntu from a CD?

My laptop (Acer Aspire 5810TZ) has a C:\ drive and a D:\ drive (ACER and DATA). If I do a clean install (is that the correct term?) of ubuntu, will it get rid of both of these drives, or will it only install to the C:\ drive, leaving the contents of the D:\ drive intact?

Further, on my C:\ drive there's a windows recovery partition... What do I do about that? Is there any way to copy that to a CD or a hard drive, just in case? 

I was thinking that I'd keep a dual-boot system, but shrink the size of the windows part. Simply, I want to be able to run stuff like Guitar Pro, and a few games without having to mess around with wine... Is that just wishful thinking? :P

As you can probably tell, I'm a total novice when it comes to installing new operating systems, and so any and all help is appreciated :) Where possible, try to keep the talk as un-technical as you can please :)

---

### Post by scorchgeek on 2011-07-31
> I've been playing around with ubuntu for about a week, and want to make it my main OS. I think I'm right in thinking that I should uninstall my wubi installation and install ubuntu from a CD?
 Yes.

> My laptop (Acer Aspire 5810TZ) has a C:\ drive and a D:\ drive (ACER and DATA). If I do a clean install (is that the correct term?) of ubuntu, will it get rid of both of these drives, or will it only install to the C:\ drive, leaving the contents of the D:\ drive intact? During the installation process, you can partition the drive however you want. In your case you would want to shrink the C drive and leave the D drive unchanged.

> Further, on my C:\ drive there's a windows recovery partition... What do I do about that? Is there any way to copy that to a CD or a hard drive, just in case? Put simply: it depends. Take a look on your start menu under the name of the manufacturer of your PC--there may or may not be an option to burn a set of discs. You can also call the manufacturer's tech support hotline and ask for a set of discs, though that might cost money. Once you get to installing Ubuntu (hopefully after getting a set of CD's somehow), I'd go ahead and delete the partition to save the space. If you leave it, you should be able to boot into the recovery partition, but all bets are off on whether the program will correctly handle your partitions when it tries to reinstall Windows.

> I was thinking that I'd keep a dual-boot system, but shrink the size of the windows part. Simply, I want to be able to run stuff like Guitar Pro, and a few games without having to mess around with wine... Is that just wishful thinking?  Not wishful thinking at all. That seems perfectly reasonable.

Finally, don't forget to back up your data before you try installing Ubuntu, just in case you make a mistake with the partitioning. Good luck and welcome to Ubuntu!

---

### Post by oldfred on 2011-07-31
Almost all new computers with win7 use all 4 primary partitions. You then have to delete one and convert it to an extended partition. The extended partition can hold many logical partitions and linux works just fine from logical partitions.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
Always have a good backup of any important data.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

---

### Post by inkrypted on 2011-07-31
In most Windows installs I have seen the D drive is your recovery partition so you might wanna check that. Most installations have a way to create a restore CD or DVD so check with Acer support to see exactly how that is done. Yeah it is probably best to do a clean install and dual boot I would install Ubuntu first and then Windows. I agree that Wine is sometimes hard to get going. My guess is that your laptop only has one hard drive and C and D are partitions so if you do a clean install using the entire drive you will loose everything.

---

### Post by B-2-10 on 2011-07-31
> **inkrypted said:**
> In most Windows installs I have seen the D drive is your recovery partition so you might wanna check that. 

I've just checked that via the disk management utility, and I've attached a screenshot just because I'm not certain what I'm looking at. I renamed my C:\ and D:\ drives a while back, just because I'm a freak for things having proper names. ACER and DATA were their original names.

Thanks for the help so far guys :) Gonna take a look at some of the suggestions in the next few days!

---

### Post by ajgreeny on 2011-07-31
It actually looks as if you have two disks in your computer, a 500GB, a 1TB and probably a 4gb usb flash drive attached, showing as disk0, disk1 and disk2.

You have some space in the 1TB disk available, which you could use, but you will need to partition some of it first to run ubuntu.

---

### Post by oldfred on 2011-07-31
+1 on ajgreeny using the second disk. It avoids a lot of issues with windows on the first disk and does not have to take up a lot of space on your second drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by B-2-10 on 2011-07-31
Sorry, should have mentioned that the 1TB hdd is my external drive. As such I'd rather not be booting an OS from it...

---

### Post by Blasphemist on 2011-07-31
The 1 TB drive is a good place to back windows up to then before you start, just good practice and keeps all your windows stuff safe. There shouldn't be any trouble doing what oldfred recommended but it's good to be safe anyway. That's exactly what my external drive was used for when I first went to dual booting. And every time since then that I've made partition changes I've made sure all my backups are current before starting.

---

### Post by sidzen on 2011-07-31
Also, suggest another partition on external created with gparted where movies may be placed.

---

### Post by waynefoutz on 2011-07-31
There should be a way to burn that recovery partition into restore disks. I would  do that BEFORE I installed Ubuntu. On machines set up this way there is usually a custom MBR (master boot record) that allows you to hit a key combination to restore the computer to it's factory state. If you mess with that, you might not be able to use that recovery partition anymore, because grub will replace that MBR.

---

### Post by oldfred on 2011-07-31
+1 on    	waynefoutz suggestion on recover disk:

Some more info on that:
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by waynefoutz on 2011-07-31
I learned that the hard way on an old Compaq desktop. I installed Ubuntu, I left the recovery partition intact, but after that it was useless, because there was no way to launch the recovery program that used the partition. I ended up having to buy the CDs from Compaq before I could sell the computer.

---

### Post by B-2-10 on 2011-08-01
Right, I've backed up an image of windows to my 1TB hdd, and I've burned a windows 7 system restore disc... Should that be enough, or would you advise any further precautions.

As I intend to do a clean install of Ubuntu, but want a dual-boot with windows 7 (on a much smaller partition) can I get some advice on how to go about doing that please?

---

### Post by oldfred on 2011-08-01
I would also make a window repairCD. The one site that we used to direct users to, does not offer a repairCD anymore. If you have to repair windows then you will need that CD. Link on how to do that in my previous post.

It looks like you have only used three primary partitions in sda. You then can shrink either c: or d: with windows MMC, but do not create any new partitions with windows. Then you can use gparted to create an extended partition with many logical partitions or can do it as part of the install. (you have that already). Reboot windows several times after shrinking to make sure it has done its chkdsk and is happy with the new size.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Lots more detail here:
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

