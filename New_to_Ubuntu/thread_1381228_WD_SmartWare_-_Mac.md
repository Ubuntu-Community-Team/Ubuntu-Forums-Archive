---
title: "WD SmartWare - Mac"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by lhb1142 on 2010-01-14
It's a very long story, but the gist is I have a Western Digital My Book Studio 1 TB External Hard Drive.

This particular hard drive [WDBAAJ0010HSL-NESN] has the ***Mac***-specific WD SmartWare installed.

Whenever I attach the drive to my Acer Extensa 5620-6419 computer (on which I have Ubuntu 9.10 installed; I use Ubuntu exclusively), two drives appear on the desktop. One is, of course, the main hard drive itself, and the other is that WD SmartWare (for Mac) which I understand is built into the firmware.

Now it's easy enough to just unmount that WD SmartWare drive every time it appears (or just ignore it altogether) but I wonder if someone has figured out a way to remove it completely (and possibly free up the space, though that's not too important as the main drive shows 930 GB free).

I can live with the WD SmartWare for Mac (it doesn't actually hurt anything) - but if someone knows how to safely remove it from the drive and would post the answer here, I would be grateful.

Thanks for reading this.

Lawrence

---

### Post by inkhorn on 2010-01-15
Hi there,

I just bought almost the same hard drive except it's not for mac.  I looked around for an answer and found a way to make Ubuntu automatically ignore the WD SmartWare virtual cd every time your computer detects the My Book coming online (full story [[COLOR="Blue"]_here_[/COLOR]]("http://nixliving.blogspot.com/2010/01/enjoy-your-wd-my-book-1tb-drive-no-more.html")).

Basically you need to add a line in your /etc/fstab file.  You may be able to copy the fstab line that I posted in my blog, but check how the virtual cd is formatted in your terminal by typing the following:

```
blkid /dev/sr1
```

sr1 is the partition label for the virtual cd.  It's such an odd label that other devices are highly unlikely to try to take it over.  Anyway, when I type the above code into my terminal I get the following output:

```
/dev/sr1: LABEL="WD SmartWare" TYPE="udf"
```

If you get the exact same output then you can literally copy the fstab line from my blog word for word.  If beside TYPE= you see "hfs" then put that in place of udf in the fstab line.

Once you put the line from my blog into your fstab file then every time your computer detects your My Book coming online it will automatically not mount the WD SmartWare virtual CD and you can go about enjoying your big external hard drive :)

Cheers,
Inkhorn

---

### Post by lhb1142 on 2010-01-15
> **inkhorn said:**
> Hi there,

I just bought almost the same hard drive except it's not for mac.  I looked around for an answer and found a way to make Ubuntu automatically ignore the WD SmartWare virtual cd every time your computer detects the My Book coming online (full story [[COLOR="Blue"]_here_[/COLOR]]("http://nixliving.blogspot.com/2010/01/enjoy-your-wd-my-book-1tb-drive-no-more.html")).

Basically you need to add a line in your /etc/fstab file.  You may be able to copy the fstab line that I posted in my blog, but check how the virtual cd is formatted in your terminal by typing the following:

```
blkid /dev/sr1
```

sr1 is the partition label for the virtual cd.  It's such an odd label that other devices are highly unlikely to try to take it over.  Anyway, when I type the above code into my terminal I get the following output:

```
/dev/sr1: LABEL="WD SmartWare" TYPE="udf"
```

If you get the exact same output then you can literally copy the fstab line from my blog word for word.  If beside TYPE= you see "hfs" then put that in place of udf in the fstab line.

Once you put the line from my blog into your fstab file then every time your computer detects your My Book coming online it will automatically not mount the WD SmartWare virtual CD and you can go about enjoying your big external hard drive :)

Cheers,
Inkhorn

Dear "Inkhorn,"

Thank you for your reply to me. Unfortunately I cannot try your solution at the present time. This Mac-formatted drive does not function properly on my Ubuntu computer as it has the HFS+ file system. While I *can* open the drive and see everything on it (and even copy what is there, at least in the WD SmartWare section - the main drive is blank), I cannot write to it. I cannot change permissions even using Nautilus.

I have researched methods of reformatting this drive (Gparted does not work) but I am not going to do it as I am now hoping to return this unit to Western Digital for an exchange. (As I said originally, it is a long story as to how I got this drive.)

If they do send me a replacement unit (using UDF files which I can access), I'll certainly try your solution - and I'll let you know the results.

Thanks again.

Lawrence

---

### Post by saltydog on 2010-01-27
@inkhorn: instead of fixing to /dev/sr1, why not using the LABEL entry in fstab?

i.e.

LABEL=WD\x20SmartWare none udf rw,noauto 0 0

If you inhibit /dev/sr1, it may happen that your DVD will never mount again...

---

### Post by saltydog on 2010-01-27
I have found a cleaner solution, waiting for Lucid (in which the bug has been fixed).

Just open with sudo grants the file:

/lib/udev/rules.d/95-devkit-disks.rules

then add the following lines:

```
ENV{DKD_PARTITION_TABLE_SCHEME}=="apm", \
  ENV{ID_CDROM}=="?*", ENV{ID_FS_TYPE}=="udf",
ENV{ID_FS_LABEL}=="WD_SmartWare", \
  ENV{DKD_PRESENTATION_HIDE}="1"
```

Devicekit will take care of this.

---

### Post by kbrowne1 on 2010-06-02
It is obvious that WD does not pay any attention to their own forum. It is full of posts about removing the stupidware partition from their external drives dating back to January and they still haven't done anything about it. I've emailed them a few times about this with no response. I mention that I am using the Linux OS. This is probably why they have ignored me.

---

### Post by JCollierDavis on 2010-06-02
Western Digital has a firmware update for this particular situation. After tremendous volume of complaints from consumers, they decided to allow the option to completely remove the second partition all together.
 
Check out this link from Western Digital.
[http://www.wdc.com/wdproducts/wdsmartwareupdate/](http://www.wdc.com/wdproducts/wdsmartwareupdate/)
 
Select your model of HDD and OS, then the "Utilities" link.  That will be the VirtualCD removing utility. 
 
It's likely that you'll need a Windows or Mac to complete the firmware update.

---

### Post by clickwir on 2010-10-13
Oh this burns me. I loved WD drives. But this StupidWare junk is really putting me off. 

Now I have to go find someone with a Windows computer that will let me install... who knows what. Hope they already have .NET installed because of those lazy programmers that need training wheels.

Install a bunch of junk, reboot, install, mess with this and that... is it really gone? I don't know. I see some posts that say it's still there and Windows is just hiding it. What about when I take this drive to another computer? Is it going to show up there and I have to run this junk all over again? This is a huge hassle. I'm ready to just return the damn thing and get something else.

Is there nothing I can do from Ubuntu to get rid of this? I'm sure I can find someone with a Windows machine, but if they'll actually let me run all this junk, I don't know.

---

### Post by lhb1142 on 2010-10-14
I should have posted the fact that Western Digital did in fact replace my drive with one which could be used as is with Ubuntu.

However this one, like most desktop WD drives, comes with that so-called backup software and, as far as I know, it cannot be removed except by someone with a great deal of know-how - not me! I too wish that if anyone does know how to remove that partition which contains the 'junk' they would post the instructions here (and without having to rely on someone's Windows computer).

But in the meantime it's all right; I just "live" with having that 'stuff' there. It doesn't hurt anything (I use my drive for storing music) so I can just ignore it.

I believe that all the newer WD drives, certainly the portable ones, still come with this unwanted software but it is easily removable (deletable) via Ubuntu. (I just received a new 500GB portable drive and I just deleted all of that software.)

---

### Post by chalkster on 2010-12-23
There are ways of completely removing the WD Smartware VCD. The long winded but well tested version is as follows ( needs windows pc ). 1) go to WD site and update drive firmware 2) make a copy of the VCD or at least the usb driver on it 3) download  and run the utility to hide VCD 4) uninstall all WD software from the PC 5) reformat drive preferably as ntfs 6) install usb driver if you dont want to see the hardware install wizard everytime you plug in the drive with windows. The drive will then work as normal with Ubuntu and you will see that the VCD has gone and its space has been reclaimed. I've done this with three My Passport drives now. The second way is much easier and can be done from Ubuntu. It will also remove the U3 partitions from Sandisk and other usb sticks as well. Plug the drive in, start GParted, unmount drive, delete all visible partitions, write new partition table, select the free space and format to whatever you want. The really important step here is to write the new partition table as this blows away everything. I can't claim this as a universal solution as I've only tried it with one drive but it should work ok.

---

### Post by exxxo45 on 2011-01-28
I got my problem SOLVED easily in Windows, but I'm not sure if this solution applies to all WD drives. 

I bought a WD My Book Essential 1.5TB as of December 2010. Got the same problem-SmartWare virtual CD would come up as another drive every time it was mounted and formatting would not change that. I solved the problem by opening a .zip file (located on the SmartWare virtual CD) named as something like this: "WDSmartWareVirtualCDManager". After accepting Licence Agreements, SmartWare disappeared and partition space was enlarged by space SmartWare took.

Simple solution for exclusive Ubuntu users remains unknown for me.

---

### Post by platz on 2011-02-11
@Inkhorn have you noticed any trouble mounting DVD media after this fix? I've just added the line as you outlined in your blog and it has worked, but I haven't tried mounting other media yet.

---

