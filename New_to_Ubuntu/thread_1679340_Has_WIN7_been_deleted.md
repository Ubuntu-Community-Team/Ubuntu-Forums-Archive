---
title: "Has WIN7 been deleted"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Earl-Grey on 2011-01-31
I installed Ubuntu 10 and think I might have somehow deleted my win7 partition or stopped it from being visible.

First I booted Ubuntu 10 with the CD and chose to go into the Ubuntu instead of installing it directly I loaded Ubuntu trial (not sure if this is the right name). Once in Ubuntu I clicked on the `Install Ubuntu 10` icon. 

There were three options to install Ubuntu and I chose the one which is alongside existing operating system. Well when installing it timed out an I powered off my computer.

Now when I switch on my computer it says `Boot error` and does nothing. I can't choose to load Win7 or linux. I can still load from my Ubuntu cd though.

Do you know if there is a way to check if my Win7 has been deleted with all my files?

---

### Post by Merk42 on 2011-01-31
Boot using the CD again, once there go to Applications > Accessories > Terminal
Once that opens up, type the following```
sudo fdisk -l
```
That will show your partitions
Paste the result in a reply


Do you have your Windows OS disc?

---

### Post by Earl-Grey on 2011-01-31
Ok, I will give that a go. I only go the computer a few months ago, it was brand new and has no Windows disk.

When Win7 was working, I could choose to do a recovery but now I just get a boot error. I will try to post my results in the new few minutes. I am loading the `Try Ubuntu` now from the CD.

I am posting this from my old computer.

---

### Post by Earl-Grey on 2011-01-31
This is what I got;

ubuntu@ubuntu:~s sudo fdisk -1
fdisk: invalid option -- '1'

Usage:
  fdisk [options] <disk> change partition table
  fdisk [options] -l <disk> list partition table(s)
  fdisk -s <partition>  give partition size(s) in blocks

Options...................................

---

### Post by Rubi1200 on 2011-01-31
Hi,
just copy/paste the command to avoid mistakes.

That is a lowercase L not 1.

---

### Post by Earl-Grey on 2011-01-31
> **Rubi1200 said:**
> Hi,
just copy/paste the command to avoid mistakes.

That is a lowercase L not 1.

Yeah, I would have done but I am using a different machine to access this forum. So I had to do it the long way.

When I look in the Disk Utility in Ubuntu, it shows that I have a 104GB partition for Linux and a 216 partition called Extended. Would this possibly be Win7?

---

### Post by Merk42 on 2011-01-31
I was expecting NTFS, not extended.
You could try [this](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/), replacing /dev/sda with whatever one had the extended partition, but I'm honestly not sure.

---

### Post by Earl-Grey on 2011-02-01
That's okay. I have tried that link but no luck.

I think if I can get the /dev/sda/1 and /dev/sda/2 swapped around I might be able to get Windows to load if it is still there.

Do you know if there is any easy way to swap them around?

[http://img695.imageshack.us/img695/1662/screenshotgg.png](http://img695.imageshack.us/img695/1662/screenshotgg.png)

I took a screen shot and sadly it looks like I have a lot of empty drives and not Win7.

---

### Post by Hedgehog1 on 2011-02-01
Earl-Grey

That screen shot of gparted tells quite a tale.  It looks like you have re-installed Ubuntu with the 'along side existing operating system' several times, each time creating more swap space partitions and unallocated partitions that would have been loaded with the Linux OS.

I am going to make a wild guess that when your computer 'stopped responding' it was in fact moving data on your Windows partition around to make room - and your turning it off left the windows partition in an unrecognizable state.

Your following attempts to load Ubuntu again didn't help, but your windows partition was destroyed when you cut the power.

---

### Post by Hedgehog1 on 2011-02-01
Earl-Grey - you said in an earlier post that you do not have the windows disk for this system.

If you don't think you can scrounge some up (by whatever means you have), they only way to restore this system to working order is to install Ubuntu one more time - but this time choose the 'use the whole disk' option (I forget the real name).

This will remove all the partitions and make just two, an ext4 for Linux and a swap space one.

As best as I can tell - your windows data is long gone now.

How were you about backing up your data?

---

### Post by Earl-Grey on 2011-02-01
> **Hedgehog1 said:**
> Earl-Grey

That screen shot of gparted tells quite a tale.  It looks like you have re-installed Ubuntu with the 'along side existing operating system' several times, each time creating more swap space partitions and unallocated partitions that would have been loaded with the Linux OS.

I am going to make a wild guess that when you computer 'stopped responding' it was in fact moving data on your Windows partition around to make room - and your turning it off left the windows partition in an unrecognizable state.

Your following attempts to load Ubuntu again didn't help, but your windows partition was destroyed when you cut the power.

Thanks for your reply. That does sound like it could be true. I just wish that there was a way of turning back the clock and I should have left win7 as it was.

Without any disks and being back to access the recovery partition I have no idea how I am going to get back. I think I will try to contact Sony to see if they have an installation disk or something to get win7 back how it used to be when I first had it.

---

### Post by Hedgehog1 on 2011-02-01
On most newer Windows systems, they make you burn a recovery CD yourself (I guess to save on costs).  It is an easy step to miss on a new computer.  Hopefully Sony will be able to send you a recovery CD.

Sorry to be the bearer of bad news...

---

### Post by Earl-Grey on 2011-02-01
> **Hedgehog1 said:**
> On most newer Windows systems, they make you burn a recovery CD yourself (I guess to save on costs).  It is an easy step to miss on a new computer.  Hopefully Sony will be able to send you a recovery CD.

Sorry to be the bearer of bad news...

No, it is better to know. Thank you!

Do you think a recovery CD would sort the problem? I am not that good at computers as you can tell, but would I need the windows disks and other applications disks or would the recovery disk have Win7 an other programmes already on it?

---

### Post by Rubi1200 on 2011-02-01
Sadly I concur with Hedgehog1's assessment of the situation; Windows is gone and Ubuntu may well be messed up too in some way.

It is also quite likely that Sony will make you pay for a recovery CD (just so you know).

I would also be careful what you tell them about all this as you don't want to do anything to void your warranty.

---

### Post by Earl-Grey on 2011-02-01
> **Rubi1200 said:**
> Sadly I concur with Hedgehog1's assessment of the situation; Windows is gone and Ubuntu may well be messed up too in some way.

It is also quite likely that Sony will make you pay for a recovery CD (just so you know).

I would also be careful what you tell them about all this as you don't want to do anything to void your warranty.

Yeah, I guess that they will charge me. 

I will try to delete the Ubuntu 10 that I installed and all other evidence ;)

Do you know the best way to delete Ubuntu 10?

---

### Post by Hedgehog1 on 2011-02-01
The name of the disk is misleading.

It 'Recovers' the PC to how it looked when it left the factory.  It really wipes out the drive and starts over.

Backups are something each of us starts doing after we lose data.  I learned the hard way, too.

An external hard drive, or a big USB stick both make good choices for baking up your data.

---

### Post by Mark Phelps on 2011-02-01
Win7 is too big to be entirely contained on a CD, so any "recovery CD", especially one provided with a preinstalled Win7 PC, is most likely only going to boot you into WinPE and then go looking for a restore/recovery image saved on the hard drive.

In many cases, preinstalled machines can be "restored" simply by pressing a function key (typically F11) that does the same thing -- boots you into a recovery mode and looks for the restore image.

If you wiped out your restore image on the drive in your hurry to install Ubuntu, then, unless you can purchase a set of full-restore CDs (or more likely today, a DVD) from Sony, there is no way to get your Win7 back.

And, next time you're in Win7, take the time to run the Backup feature that will create and burn a Win7 Repair CD. You will need that if you are going to mess around with dual-booting.

---

### Post by Earl-Grey on 2011-02-01
> **Hedgehog1 said:**
> Earl-Grey - you said in an earlier post that you do not have the windows disk for this system.

If you don't think you can scrounge some up (by whatever means you have), they only way to restore this system to working order is to install Ubuntu one more time - but this time choose the 'use the whole disk' option (I forget the real name).

This will remove all the partitions and make just two, an ext4 for Linux and a swap space one.

As best as I can tell - your windows data is long gone now.

How were you about backing up your data?

Thank you again for the reply Hedgehog!

After contacting Sony today, I don't think that they will hand me a recovery CD, one of their engineers needs to have a look at it. The lady said that most people would use the recover partition on the same drive and don't need a recovery disk, but I explained that that was also gone.

I know that I could still keep Ubuntu on the system, but I am afraid that Sony will say `You shouldn't have been messing about with a new OS, so we can't recover your system`. I would like to keep it a secret so hopefully they will fix it for free.

I totally erased Ubuntu and all other partitions, and when I boot, I see a blank screen with the flashing text marker. 

Will let you know if Sony fix it for free. Wish me good luck :KS

---

### Post by Earl-Grey on 2011-02-02
Found out that Sony do have recovery disks and it will cost a big $85. If I had somebody to have a look at it it would be an extra $100 even though it is only a few months old.  So I have ordered the recovery disk. The 1 year guarantee does not cover any software issues only hardware.

I just hope that the recovery disk brings back the system to its former glory .

---

### Post by Hedgehog1 on 2011-02-02
> **Earl-Grey said:**
> Found out that Sony do have recovery disks and it will cost a big $85. If I had somebody to have a look at it it would be an extra $100 even though it is only a few months old.  So I have ordered the recovery disk. The 1 year guarantee does not cover any software issues only hardware.

I just hope that the recovery disk brings back the system to its former glory .

At $85 for the recovery disks - I wonder if you would not be better off buying Windows 7 again. Then at least you would be able to install it on a real or VM ware box.  If you have the 'Microsoft XP' stickers on your previous PC with an activation code, you qualify for the upgrade price.

The Sony disk will have drivers for you laptop - although you can usually download drivers.

just a thought...

---

### Post by kaldor on 2011-02-02
If this is the case, maybe you have the perfect chance to give Ubuntu a shot for a while :)

Try a solely Ubuntu computer until you find you need the Windows discs. You may find it works out for you in the end and may save some money.

---

### Post by Earl-Grey on 2011-02-03
Yes it is quite a lot and it would be cheaper to get windows. I do have the Win7 serial number e.t.c but think for easiness I will just pay for the recovery disk. Next time I will be sure to make a back up/recovery disk beforehand myself.

I actually like playing a few games on my PC like Fifa or Call of Duty 4. If I used Ubuntu I think it would be quite difficult to get these games to work, so that it why I wanted to have Windows and Ubuntu running together. So I could use Win7 for gaming and Ubuntu for anything else.

---

### Post by Mark Phelps on 2011-02-03
> **Hedgehog1 said:**
> At $85 for the recovery disks - I wonder if you would not be better off buying Windows 7 again. .

Don't know of anywhere you can purchase Win7 for anything close to that amount.

Also, the Sony restore media will include the drivers needed for that PC.

So, it's actually quite a bargain.

---

### Post by Earl-Grey on 2011-02-09
I finally got my recovery disks in the post today. I was surprised to find not just 1 or 2 disks but 5 of them. It took me about 30 minutes to get my system up to its former glory. Now if I make a mistake installing Ubuntu or something, I always have those disks as a safe guard.

Thank you all for your great advice, even thought it wasn't directly to do with Ubuntu :popcorn:

---

