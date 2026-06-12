---
title: "Increasing the size of a windows partition."
date: 2010-12-31
forum: New to Ubuntu
---

### Post by Jonas thomas on 2010-12-31
My E71 smartphone uses some windows based software which I installed on my dual-boot machine. (The software automatically converts the mp4 to be viewable on the phone, which was a problem I was having when I was in linux)  At the time I partitioned the drive it never occurred to me that I would be downloading mp4 on the windows side. ;(  

Anyway, I found this link: [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions") which seems to be informative. The only thing is that it's more focused on making windows smaller.  As much as it pains me, I need to go in the other direction(make windows bigger/linux smaller).  Can anyone recommend the ultimate step by step link on how to do that? (I have 10.04 on the linux side and XP home on the other.

Thanks all. 
Happy New Year.
JT

---

### Post by doperative on 2010-12-31
"GParted is a free partition editor for graphically managing your disk partitions."

[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by TeoBigusGeekus on 2010-12-31
Would you like to try to convert mp4s to your phone's format using linux?

---

### Post by Paqman on 2010-12-31
> **Jonas thomas said:**
> 
Anyway, I found this link: [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions") which seems to be informative. The only thing is that it's more focused on making windows smaller.  As much as it pains me, I need to go in the other direction(make windows bigger/linux smaller).  Can anyone recommend the ultimate step by step link on how to do that? (I have 10.04 on the linux side and XP home on the other.


The process is exactly the same. Boot up into a LiveCD and use Gparted to shrink your Linux partition(s) and expand your Windows one. Gparted is already installed on the standard Ubuntu LiveCD so you can just use that.

Since you already have a swap partition on the drive the LiveCD will automatically mount it to improve performance, the problem is that this actually prevents you from making changes to your Linux partitions. The simple solution in Gparted is to right click on your swap partition and "swapoff".

---

### Post by Jonas thomas on 2010-12-31
> **TeoBigusGeekus said:**
> Would you like to try to convert mp4s to your phone's format using linux?

I appreciate the offer but I've been down that route.[URL="http://ubuntuforums.org/showthread.php?t=1645138"]
http://ubuntuforums.org/showthread.php?t=1645138[/URL]

I spent a few days trying to get that to work.  Nokia's pc suite does a nice job of making the conversions so that the video's just plain work.  I tried to make some conversions with Linux I just couldn't find the write settings.  On the Linux side I was only able to access the card memory while the PC suite gives me access to phone memory some other features, so I think I'm stuck on the windows side for this.

I find it ironic that the OS on the Nokia E71 is Linux and that Nokia owns trolltech which has the cross platform Gui QT.  Yah think that there application software in interphase with the phone would be a cross platform app, but apparently it's not.  Go figure.

---

### Post by Jonas thomas on 2011-01-01
> **Paqman said:**
> The process is exactly the same. Boot up into a LiveCD and use Gparted to shrink your Linux partition(s) and expand your Windows one. Gparted is already installed on the standard Ubuntu LiveCD so you can just use that.

Since you already have a swap partition on the drive the LiveCD will automatically mount it to improve performance, the problem is that this actually prevents you from making changes to your Linux partitions. The simple solution in Gparted is to right click on your swap partition and "swapoff".

Ok... I managed to shrink my linux partition but I haven't been able to get my windows partition to grow.  I have my windows partition in /dev/sda1 and my unallocated space seems to be in dev/sda2.   When I click on my /dev/sda1 and click on resize/move I don't show space available beyond what I already had.  I don't know what to do here.:confused:
[Edit] I think I got it. I just need to click out the outer block to resize.

---

### Post by waynefoutz on 2011-01-01
One important suggestion: When you change the size of your Windows partition, Windows will run scandisk. Don't interrupt that process, let it finish. I fried a Windows install that way.

---

### Post by Paqman on 2011-01-01
> **Jonas thomas said:**
> 
[Edit] I think I got it. I just need to click out the outer block to resize.

Yep, you need to shrink that extended partition that all your Linux stuff is inside, then expand the NTFS partition into the space created.

---

### Post by nikefalcon on 2011-01-01
[QUOTE="Jonas thomas"][Edit] I think I got it. I just need to click out the outer block to resize.
[/QUOTE]

The unallocated space is inside the logical partion- sda2. Try to resize it(I dont have a 100% success rate;) ) If that doesn't work then use the unallocated 26.88GiBs to make a new partition. FAT and NTFS are accessible through ubuntu and windows so you can use the space more efficiently. Or if want a separate ext partition for linux......do it your way! 
The best config is the one that works for you! :)

---

### Post by Jonas thomas on 2011-01-01
> **Paqman said:**
> Yep, you need to shrink that extended partition that all your Linux stuff is inside, then expand the NTFS partition into the space created.

Thank you everyone for the advice.  I think I got everything resized properly.

Only advice I have to had to give is to have patience and something else to do while doing this,  This is a very slow process.  I wonder if you the swap space needs to be switched to swap off only when that space is being moved. (seemed to work).


Happy new year...
JT

---

### Post by Paqman on 2011-01-02
> **Jonas thomas said:**
> 
Only advice I have to had to give is to have patience and something else to do while doing this,  This is a very slow process.

Indeed it is. Magnetic hard drives are painfully slow, as doing a really disk-intensive task like this highlights.

Luckily however, SSDs are starting to replace magnetic drives, and will make doing this kind of job a lot quicker and nicer.

---

