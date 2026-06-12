---
title: "Cannot partition NTFS drive"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by MaxFlight on 2009-01-25
I'm trying to turn my old XP Dell laptop into a dual-boot machine. I don't have any problem running Ubuntu from the live disk, but when I try to install Ubuntu I can't partition the internal hard drive. (Which was replaced last year.)

The partition step only gives me the option of replacing the entire existing NTFS partition. I see where others have been advised to run chkdsk, defrag the disk, and reboot Windows cleanly.  I've done all those things several times. Still, it won't let me specify anything other than a new partition spanning the entire disk.

There must be something simple I just don't get. Any advice on how I can work through this?

---

### Post by kestrel1 on 2009-01-25
Do you get the custom option during the partition process?

---

### Post by MaxFlight on 2009-01-25
> **kestrel1 said:**
> Do you get the custom option during the partition process?

Yes I did, and even there I could not create a new partition that was less than the full disk.

---

### Post by hamdi on 2009-01-25
what if you create linux partition in windows and then install ubuntu to newly created partition before.

---

### Post by howefield on 2009-01-25
Boot to the desktop from the live cd and use Partition Editor from the system > administration menu to resize your ntfs partition to leave enough space for your Ubuntu install. 

Then tell the installer to use the free space.

---

### Post by Elfy on 2009-01-25
Does gparted - System > Admin > Partition Editor let you do it?

If so make the partitions before you start the install and use manual.

Alternatively download a partition editor, burn as an iso and boot with it. I use [partedmagic]("http://partedmagic.com/").

---

### Post by kelean on 2009-01-25
I had that problem a few weeks back.  I had bought a computer off of ebay that had winXP preinstalled.  I was not able to repartition at first.  You might need to run chkdsk /r from windows.  It worked for me.

---

### Post by MaxFlight on 2009-01-25
> **howefield said:**
> Boot to the desktop from the live cd and use Partition Editor from the system > administration menu to resize your ntfs partition to leave enough space for your Ubuntu install.

OK, I tried that: Running GParted from the admin menu, I clicked on the single ntfs partition, then clicked Resize/Move.  I can't drag the ends of the green outlined box at all. The Free Space Preceeding, New Size, and Free Space Following values cannot be changed. Both Free Space's say zero.

---

### Post by bumanie on 2009-01-25
Personally, I found that the dedicated gparted live cd does a better job than the one that comes with ubuntu. I have had problems with ntfs resizing from ubuntu, but never with the live gparted cd. [get it here]("http://gparted.sourceforge.net/download.php")

---

### Post by MaxFlight on 2009-01-25
I got the partedmagic iso, burned the CD, and booted from that.  GParted in that gives the same results I noted previously.

Now when I looked at partition > information, I see a warning that "The disk has a bad sector" and I should run 'chkdsk /f /r' and reboot twice.

I've done that before, but I guess I'll do that again, all the while thinking about that definition of insane. ("Doing the same thing over and over and expecting different results.")

---

### Post by kelean on 2009-01-25
I have a thread on this same problem I tried to link to the thread but it did not work.  I will try again.

[http://ubuntuforums.org/showthread.php?t=1017684]("http://ubuntuforums.org/showthread.php?t=1017684")

---

### Post by MaxFlight on 2009-01-26
Still no luck. I've defraged the hard disk with the Windows disk cache disabled - that moved _everything_ to the left except some "cannot move" sectors in about the middle. (Is that a clue?) I've run chkdsk. I've run gparted standalone outside the Ubuntu live disk. Still I cannot shrink the NTFS partition to make space for Ubuntu.

So unless somebody can think of something I should try, I guess I'll reformat the disk, reinstall XP (ugh), and try again from scratch.

Thanks, all.

---

### Post by vanadium on 2009-01-26
Before doing that, show us your current partitioning. It might be that the installer cannot create additional partitions without removing at least one partition. In the life CD, open the terminal and type

```

sudo fdisk -l

```
Copy/paste the output here.

---

### Post by Elfy on 2009-01-26
Also it 'might' be hiberfil - in which case turn of hibernate

---

### Post by blackgr on 2009-01-26
propably you need to install ntfsprogs to be able to edit ntfs partitions.
```

sudo apt-get install ntfsprogs
```

and try to partition with gparted once more

---

### Post by wangsuda on 2009-01-26
On a related note, is it possible to increase the space Ubuntu 8.10 takes up on a hard drive? When I originally installed it, I did the default 10 gig. I would like to increase it.

---

### Post by blackgr on 2009-01-26
just boot from the live cd and run gparted. there just by minimizing other partitions you will be able to increase the space

---

### Post by wangsuda on 2009-01-26
> **blackgr said:**
> just boot from the live cd and run gparted. there just by minimizing other partitions you will be able to increase the space

Thanks, I'll try that.

---

### Post by MaxFlight on 2009-01-26
> **vanadium said:**
> Before doing that, show us your current partitioning. It might be that the installer cannot create additional partitions without removing at least one partition. In the life CD, open the terminal and type

```

sudo fdisk -l

```
Copy/paste the output here.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a098a09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

Does that tell us something?

(Thanks!)

---

### Post by Elfy on 2009-01-27
Vanadium was wanting to check that you didn't already have the maximum amount of partitions - you don't.

Have you looked to see if you have a hiberfil. file in C:\ - that can sometimes get in the way of partitioning - turn of hibernate to remove it.

---

### Post by MaxFlight on 2009-01-27
> **forestpixie said:**
> Vanadium was wanting to check that you didn't already have the maximum amount of partitions - you don't.

Have you looked to see if you have a hiberfil. file in C:\ - that can sometimes get in the way of partitioning - turn of hibernate to remove it.

Yes I did have a hiberfil file! I've turned that off, defragged again, and rebooted.  (For others, [http://www.softwarepatch.com/tips/hiberfil-sys-xp.html]("http://www.softwarepatch.com/tips/hiberfil-sys-xp.html") explains what it is and how to turn it off in XP.)

Since I'd run 'sudo apt-get install ntfsprogs' the green outlined box in Gparted (I'm back on the live CD) has turned into a solid green bar, and I can't now see how to resize the ntfs partition. New Partition is greyed out. Edit Partition seems to act on the whole ntfs partition.

Sorry to be so stupid...

---

### Post by Elfy on 2009-01-27
Once you click the resize button - there should be handles at either end - clikc end with mouse and move it, the size should then change.

Once it's at the right size - Apply

Then you'll be able to do what you want

You won't be able to make a new partition until there is room

---

### Post by MaxFlight on 2009-01-27
> **forestpixie said:**
> Once you click the resize button - there should be handles at either end - clikc end with mouse and move it, the size should then change.

Once it's at the right size - Apply

Then you'll be able to do what you want

You won't be able to make a new partition until there is room

Now in Parted Magic: I select that ntfs partition and click Resize/Move. When I hover over the handle on the right (the triangle) the cursor turns into the left/right arrow. I hold the right mouse button and try to drag it, the cursor moves but the partition does not.

Exiting out of that, I click Partition > Information, and I still get that 'WARNING: The disk has bad sector' message. I've run chkdsk many times - tho not since getting rid of the hibernate file. Maybe that's the problem...

---

### Post by Elfy on 2009-01-27
Not sure tbh - longtime since I had anything much to dowth ntfs

Try to chkdsk again and boot win again - the command you had earlier chkdsk /r/f or somesuch ...

---

### Post by kestrel1 on 2009-01-27
I would suggest downloading the diagnostic tools for your particular make of hard drive & make sure that there are no defects. It could be that the drive is on the way out.

---

### Post by MaxFlight on 2009-01-27
> **kestrel1 said:**
> I would suggest downloading the diagnostic tools for your particular make of hard drive & make sure that there are no defects. It could be that the drive is on the way out.

I downloaded and ran the Seagate diagnostics - it found and repaired 16 errors. Don't know why chkdsk didn't find them. Still, I'm still unable to shrink the ntfs partition to make free space. Just for haha's I also defragged again, ran chkdsk, and rebooted windows twice. Still the same result: Gparted won't change the ntfs partition.

I know there is an explanation, and experience tells me the harder it is to find, the more likely it is I'm doing something dumb.  I have to get this to work!

---

### Post by Elfy on 2009-01-27
Not at all sure what is going on here - but you could try posting on the gparted forums. I've not used that one myself - but I know of at least one member here who has.

---

### Post by kestrel1 on 2009-01-27
I don't suppose you have access to Partition Magic? You could try that if Gparted is failing.

---

### Post by MaxFlight on 2009-01-27
Thanks, guys. I'll look for the gparted forum. I thought about Partition Magic (Leo raves about it all the time) but then I saw that it's not very cheap - and I am! Since it's my old laptop and not my main Windows box, I might just let the Ubuntu install take the whole thing. I'm getting antsy and want to get started learning Linux!

---

### Post by MaxFlight on 2009-01-29
In the seventies while writing PL/1 code for a mainframe IBM, I learned that once you reached a certain point trying to debug a routine, there was only one thing left to do: Throw out the code and re-write it from scratch. It almost always worked.

I re-installed XP in it's own partition and left the rest free. After that, Ubuntu installed without a hitch. No problem creating the new partitions.

I'm now off and running with Ubuntu.

Thanks to all who offered help and suggestions. I learned a lot, which is kinda the whole idea here.

---

