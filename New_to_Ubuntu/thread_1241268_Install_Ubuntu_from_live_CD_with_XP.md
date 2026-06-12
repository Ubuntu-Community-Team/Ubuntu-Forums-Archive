---
title: "Install Ubuntu from live CD with XP"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by zdubun on 2009-08-15
Hi there,

I am totally new. I got a Live Ubuntu 9.04 DVD. My windows XP shows that about 90 GB of my 120gb hard drive is free. However when I try to install Ubuntu, the partitioner shows 45 gb occupied by windows and 60 GB occupied by dev/sda5 with only 2.5GB free.

What does it mean? how shall I install Ubuntu side by side with XP?

Thank you.

---

### Post by LewRockwell on 2009-08-15
> **zdubun said:**
> Hi there,

I am totally new. I got a Live Ubuntu 9.04 DVD. My windows XP shows that about 90 GB of my 120gb hard drive is free. However when I try to install Ubuntu, the partitioner shows 45 gb occupied by windows and 60 GB occupied by dev/sda5 with only 2.5GB free.

What does it mean? how shall I install Ubuntu side by side with XP?

Thank you.

It might be helpful to us to see a screenshot of your partition editor

.

---

### Post by pedro3005 on 2009-08-15
You have to repartition it, as Windows and Linux can stay on the very same partition. Use GParted (System - Administration - Partition Editor) to resize the Windows partition, create a new one using freed space, format it to EXT3. Make ubuntu install on that one, it should work.

---

### Post by zdubun on 2009-08-15
Thanks, but just to show how new am I , how do I take a screen shot?

---

### Post by LewRockwell on 2009-08-15
> **zdubun said:**
> Thanks, but just to show how new am I , how do I take a screen shot?

While booted in ubuntu via LiveCD you will go to:

Applications->Accessories->Take Screenshot

and you should be able to figure it out from there

this is assuming you're able to use that same LiveCD Ubuntu session to post to this forum(since the screenshot is only saved for that session...of course you could save it to a thumb drive to carry to another computer as a last resort)

Also, when you make the post where you want to attach the screenshot file you just scroll down to the "Additional Options" and click on "Manage Attachments" in the "Attach Files" area

.

---

### Post by zdubun on 2009-08-15
Thanks a lot, will get around to doing it. Will be coming to the forum later hopefullly with the screen shot

---

### Post by nhasian on 2009-08-16
it might be easier if you just copy and pasted the output of:

```
sudo fdisk -l
```

```
df -ah
```

```
sudo parted -l
```

---

### Post by zdubun on 2009-08-16
Hi there,

I am posting a windows paint representation of the harddrive as shown by ubuntu installer. For some reason I could not get on the net from the ubuntu live cd.[IMG]file:///C:/DOCUME%7E1/Welcome/LOCALS%7E1/Temp/moz-screenshot.png[/IMG][IMG]file:///C:/DOCUME%7E1/Welcome/LOCALS%7E1/Temp/moz-screenshot-1.png[/IMG][IMG]file:///C:/DOCUME%7E1/Welcome/LOCALS%7E1/Temp/moz-screenshot-2.png[/IMG]

Sorry could not do it. So that shows how much I know about computers.

Anyway, it shows 48.8 GB sda1 as occupied by windows XP(Blue colour). Then 60.5 GB as dev/sda5. Only 2.5 GB free. 

I have no downloaded tracks, no movies and only PDF files. According to Windows about 90 GB of hard drive is free.  The 120 GB hard drive is divided in to C and D.

I appreciate all the help.

---

### Post by nhasian on 2009-08-16
well if you dont store anything on your D drive, you can put ubuntu on that partition.

I would really feel more comfortable if you could give us the output of the commands i mentioned in my previous post.  if you are unable to access the internet from the liveCD, at least you can copy/paste the output to a text file.  then you can paste the data output here when you have an internet connection.

---

### Post by Paddy Landau on 2009-08-16
> **pedro3005 said:**
> You have to repartition it, as Windows and Linux can stay on the very same partition. Use GParted (System - Administration - Partition Editor) to resize the Windows partition, create a new one using freed space, format it to EXT3. Make ubuntu install on that one, it should work.
Woah! If you resize the Windows partition with Gparted, you run a serious risk of corrupting your Windows drive. Resizing NTFS partitions is buggy with Gparted.

It's possible that your computer came with a C: drive and a D: drive. Many manufacturers (e.g. Toshiba) do that, I don't know why.

Boot into Windows, and check whether you have an empty D: drive.

Also paste the results of those commands as previously requested.

Don't try to repartition your drive until we've figured out what's going on.

---

### Post by nhasian on 2009-08-16
> **Paddy Landau said:**
> Woah! If you resize the Windows partition with Gparted, you run a serious risk of corrupting your Windows drive. Resizing NTFS partitions is buggy with Gparted.

I'm afraid i have to disagree.  gparted does an excellent job of resizing ntfs partitions.  i've done it dozens of times myself without any problems with both windowsXP as well as WindowsVista.  Of course I always recommend backing up before modifying partitions.  There is an inherent risk in resizing volumes, but I wouldnt say its a serious risk :)  its far more likely for a user to delete the wrong partition or to resize a mounted volume which corrupts the data...

---

### Post by Bartender on 2009-08-16
When you ask Windows about "free space" it will tell you about NTFS disk space that is not storing data.

When you pop in the Ubuntu CD and get to the partitioner, or pop in a GParted LiveCD, they report file systems.  They will also indicate used space, but that's secondary to their main goal, which is to identify file systems.

So it's completely understandable that Windows would say you have free space, and the Ubuntu CD would say that you do not.  Actually, it's a bit odd that Ubuntu would indicate any free space at all.  

The easiest way to give us a screenshot - boot into the Live CD.  When it's done and you have the desktop, plug in a thumb drive.  Unless you are having a really bad day, the thumb drive will show up as a device on the desktop.  Now go to System>Administration and bring up the partitioner.  Once you have that up on the screen, go to Applications>Accessories>Screenshot and take a picture of the whole screen.  Type in a 5 second delay.  When the screenshot is taken, save it, but browse to the thumb drive and save it there.  Then get out of the LiveCD, boot back into Windows, come back to this post, and follow the directions for managing attachments.  The "Attach Files" box is underneath the body of the reply screen.  I attached a screenshot to show you.

---

### Post by zdubun on 2009-08-16
Hi all,

Whether  my problem gets solved or not, it has been a pleasant experience coming to the ubuntu forums, seeing from the help I am getting.  Thanks to everybody in advance.

---

### Post by Paddy Landau on 2009-08-17
> **nhasian said:**
> I'm afraid i have to disagree.  gparted does an excellent job of resizing ntfs partitions...
There are many posts on this forum advising against it. I myself have done this just three times, twice successfully and once losing my Windows (but I'd made a backup first, knowing the risks involved).

Actually, having written that, I wonder whether this applies to all NTFS partitions or only to those that have Windows installed?

I read somewhere that installing ntfsprogs will make gparted more reliable.

To resize Windows partitions, you are strongly advised to use the partition resizer built into Windows.

---

### Post by nhasian on 2009-08-18
> **Paddy Landau said:**
> 
To resize Windows partitions, you are strongly advised to use the partition resizer built into Windows.

Good luck with that.  first of all you cannot shrink volumes in Windows XP.  So it has to be Vista or Windows 7.  second even if you have vista and go to the disk manager and select the shrink volume tool it may give you 5 or 7 gigs to use.  even if you have 70 gigs free on the hard disk!  I've seen this happen several times.  its a piece of crap.  I know I know, I've defraged the drive twice.  I've told windows not to use a paging file, and i deleted the 2.5 gig pagefile.sys from the c: drive.  i've followed all the instructions i could find online to get the shrink volume to allocate more space but its just rubbish.  Gparted has worked for me every time and its never screwed up for me.  I've used it on NTFS drives in both Windows XP and Windows Vista on the primary hard disk where windows resides.

the only thing after you resize the ntfs partition and reboot, when windows starts it detects something is different and runs a scandisk automatically, but everything always comes out kosher.

---

### Post by Paddy Landau on 2009-08-18
> **nhasian said:**
> parted has worked for me every time...Thanks for some good points. You're one of the lucky ones.

There are third-party shrink methods that are designed for Windows; I used one once, I forget its name. Check the Windows Community forums for software that will help.

If you are going to use gparted to shrink, then do a full backup. You can back up your entire partition using [PartImage]("http://www.partimage.org/") (use [SysRescCD]("http://www.sysresccd.org/"), which comes with PartImage, to do this), or using [CloneZilla]("http://clonezilla.org/"), and for safety also do a normal full backup.

Although gparted is a reliable partition manager, there is always the chance that it will lose data (as has happened to me).

---

