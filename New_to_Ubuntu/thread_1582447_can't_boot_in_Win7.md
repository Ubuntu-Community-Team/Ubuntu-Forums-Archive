---
title: "can't boot in Win7"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by sallam on 2010-09-26
Greetings

I had a nightmare today, and its still going!

I've installed ubuntu about 5 days ago. Each time I start my laptop it asked me which OS I want to start with. It was only today that I tried selected Win7, but it just kept reloading the boot loader giving the same choices. The one I was selecting is "Windows 7 (loader).

So, I re-installed ubuntu again thinking it could be fixed then. I also chose the advanced selection like before, where I get to choose the specific partition to install ubuntu in (my HDD has 5 partitions). But this time, I selected the first choice in boot loader drop-down menu (the first being the hard disk itself, and the second choice, which I selected the first time, was Win7 loader). But after installation, it gave error when I tried to access my Win7.

So, I reinstalled, this time trying the simple first choice, "side-by-side, to choose which one each restart". But this choice resulted in the complete disappearance of the boot loader. Now the laptop starts directly in ubuntu, offering no choice and showing no boot loader! not just that, but even my windows partitions are not there anymore in ubuntu Places.

What do I do now?

I need to be able to boot in win7 every once in a while..

---

### Post by sandyd on 2010-09-26
> **sallam said:**
> Greetings

I had a nightmare today, and its still going!

I've installed ubuntu about 5 days ago. Each time I start my laptop it asked me which OS I want to start with. It was only today that I tried selected Win7, but it just kept reloading the boot loader giving the same choices. The one I was selecting is "Windows 7 (loader).

So, I re-installed ubuntu again thinking it could be fixed then. I also chose the advanced selection like before, where I get to choose the specific partition to install ubuntu in (my HDD has 5 partitions). But this time, I selected the first choice in boot loader drop-down menu (the first being the hard disk itself, and the second choice, which I selected the first time, was Win7 loader). But after installation, it gave error when I tried to access my Win7.

So, I reinstalled, this time trying the simple first choice, "side-by-side, to choose which one each restart". But this choice resulted in the complete disappearance of the boot loader. Now the laptop starts directly in ubuntu, offering no choice and showing no boot loader! not just that, but even my windows partitions are not there anymore in ubuntu Places.

What do I do now?

I need to be able to boot in win7 every once in a while..
you resized the windows partition using ubuntu eh?

don't do that.  -> [https://help.ubuntu.com/community/RecoveringWindows#How%20To%20Recover](https://help.ubuntu.com/community/RecoveringWindows#How%20To%20Recover)

---

### Post by sallam on 2010-09-26
No, I didn't. But it seems that ubuntu did by itself when I selected 'side-by-side' option.
But why did the boot loader disappeared from startup?
Should I re-install win7 or what?
o there a way to fix the boot loader to show up again?

---

### Post by sandyd on 2010-09-26
> **sallam said:**
> No, I didn't. But it seems that ubuntu did by itself when I selected 'side-by-side' option.
But why did the boot loader disappeared from startup?
Should I re-install win7 or what?
if you do the side by side option, you are resizing the windows partition. as said in the article, this screws up windows because its bootloader sucks.

the link ive provided gives recovery instructions.
but first, post the output of
```

sudo fdisk -l
```
YOu may be harboring more than 1 ubuntu installation.
In the future, do these steps -> [https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows]("https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows")
and then when installing ubuntu, choose "use largest block of free space"

---

### Post by sallam on 2010-09-26
Many thanks. Here is the output:

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aafef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14212   114149376   83  Linux
/dev/sda2           14212       14594     3068929    5  Extended
/dev/sda5           14212       14594     3068928   82  Linux swap / Solaris


My win 7 is in C, which is 40GB. My ubuntu was in F, which was 12GB, and I deleted it, then made 1 partition of 10GB out of it, and the rest, 2GB for swap. The last time I installed ubuntu, I deleted the 10GB partition, to make sure there is no 2 ubuntus. And I thought it would use that free space, but it seems I was wrong..

---

### Post by sandyd on 2010-09-26
> **sallam said:**
> Many thanks. Here is the output:
thats not good.....
there is no windows 7 installed at the moment.
I guess it would be better to start from scratch on this one.
do this

Go to System -> Administrative -> Gparted. in a livecd.

There should be 3 partitions. One is primary, one is extended, and one is swap.

Right click on the swap and select "swapoff"
Now, right click the swap and delete it.
Delete the extended, and the primary partition.

Now, install windows and follow the instructions from here -> [https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)
to install ubuntu

---

### Post by sallam on 2010-09-26
I lost the whole data in my HDD, including my years of personal files and family photos and videos..
I will never trust ubuntu again. Ever.
There should be clear details in ubuntu's installation options.
How come they say: side-by-side, when their real intent is to wipe the whole HDD off?!!!

Shame on you ubuntu. I'll never forgive you.
From now on, anyone who installs ubuntu with none other than a blank system deserves what they'll get.

---

### Post by thatguruguy on 2010-09-26
> **sallam said:**
> I lost the whole data in my HDD, including my years of personal files and family photos and videos..
I will never trust ubuntu again. Ever.
There should be clear details in ubuntu's installation options.
How come they say: side-by-side, when their real intent is to wipe the whole HDD off?!!!

Shame on you ubuntu. I'll never forgive you.
From now on, anyone who installs ubuntu with none other than a blank system deserves what they'll get.

Don't bother to reply to this topic.

I think what you meant to write was, "Anyone who installs ubuntu (or, for that matter, any other OS) without first backing up their data deserves what they'll get."  Which is an absolutely true statement.

---

### Post by Mark Phelps on 2010-09-26
> **sallam said:**
> I lost the whole data in my HDD, including my years of personal files and family photos and videos..

Not necessarily ...

If you can remove your hard drive and connect it to another PC as an external drive, then go to the Runtime Software site and download their free version of GetDataBack for NTFS.  Install it on the machine to which the drive is connected as an external.

Then, run it.  It won't recovery the files, but it will indicate what files it found and what your chances are of successfully recovering them.

To do the actual recovery, you have to purchase the software.

But, it's your files ... and it's your money.

---

### Post by lbrty on 2010-09-26
If you want to recover your files for free, try Recuva. I have used it to recover files for friends and it works really well. Lastly, always remember to backup your data prior to upgrading/installing any operating system.

[http://piriform.com/recuva](http://piriform.com/recuva)

> Runs on Microsoft Windows 7, Vista, XP and 2000. Including both 32-bit and 64-bit versions.

---

### Post by jtarin on 2010-09-26
> **sallam said:**
> I lost the whole data in my HDD, including my years of personal files and family photos and videos..
I will never trust ubuntu again. Ever.
There should be clear details in ubuntu's installation options.
How come they say: side-by-side, when their real intent is to wipe the whole HDD off?!!!

Shame on you ubuntu. I'll never forgive you.
From now on, anyone who installs ubuntu with none other than a blank system deserves what they'll get.

Don't bother to reply to this topic.While I can agree with you in spirit....I will disagree with you in intent. While a fuller explanation could be warranted....where does such an explanation start and when does it end for the sake of install dialog. As in anything we touch today....Buyer Beware. Today as much as 13 years ago when I started dabbling in Unix/Linux it pays to RTFM. Today we have the opportunity to have at our fingertips a wealth of knowledge from all those that have gone before.....it is ours for the taking. Yesterday not much documentation was available.

---

### Post by wilee-nilee on 2010-09-26
bummer

---

### Post by presence1960 on 2010-09-26
[https://help.ubuntu.com/10.04/switching/C/index.html](https://help.ubuntu.com/10.04/switching/C/index.html)

then see here:

[https://help.ubuntu.com/10.04/switching/C/first-steps.html](https://help.ubuntu.com/10.04/switching/C/first-steps.html)

Note question #2!

You have learned a valuable lesson the hard way. never, NEVER, **_[SIZE="6"]NEVER[/SIZE]_** _perform partitioning or OS installations without first backing up your important data!!_

I always recommend that those who are not familiar with Linux and partitioning in general do a lot of reading and studying prior to installing Linux.

Sorry to hear about your loss, however that was caused by operator error/ignorance. You really should have studied the task you were about to undertake and should have backed up your data first.

I guess it is easier to blame ubuntu rather than take responsibility for your own actions. One day you will see that it was your fault not ubuntu's. For even if the error was caused by ubuntu or by you the fact is that you disregarded the most basic tenet when it comes to installing an OS and /or partitioning- that is to back up your data. I really have no empathy for you especially after bashing ubuntu for your ineptitude.

P.S. I see in your signature you are running 10.10. You are warned with alpha and beta stage that installing this software in a production machine is not recommended.

---

### Post by Jerry N on 2010-09-26
> **presence1960 said:**
> NEVER[/SIZE]_** _perform partitioning or OS installations without first backing up your important data!!_ 

I disagree - One should never quit for the day without backing up everything important!!!!!  I have no sympathy whatsoever for anyone that loses data because they were too lazy to back it up.  Unfortunately, long experience tells me that most people have to lose something important before they learn that lesson, no matter how many times they have been told. I backup to a second internal HD, then periodically to USB drive, and the really important stuff (gigabytes of pictures) is on a hard drive in a safety deposit box.  Paranoia is a virtue!

Jerry

---

### Post by presence1960 on 2010-09-27
> **Jerry N said:**
> I disagree - One should never quit for the day without backing up everything important!!!!!  I have no sympathy whatsoever for anyone that loses data because they were too lazy to back it up.  Unfortunately, long experience tells me that most people have to lose something important before they learn that lesson, no matter how many times they have been told. I backup to a second internal HD, then periodically to USB drive, and the really important stuff (gigabytes of pictures) is on a hard drive in a safety deposit box.  Paranoia is a virtue!

Jerry

Most people are too lazy to have a back up plan in place & use it. I have an internal hard disk onto which I back up daily using rsync. Then I have an external USB disk that stays unplugged from my machine except for the weekly backup I make again using rsync. I also have images of all my OS partitions on the external disk using clonezilla.

I feel secure in my back up plan because what are the odds of 3 hard disks going at once? I have the original data, a copy on an internal hard disk and a copy on an external usb along with images of my OSs. One back up disk would suffice for most people, but I leave nothing to chance. If the OP doesn't learn his lesson now he never will. Computers, more specifically hardware (such as hard disks) are machines. As with the rest of machines they are subject to failure and breakdown. Protect your data. Have a back up plan and use it regularly. If you are too lazy to do so at least make a backup when installing an OS or partitioning. You definitely do not want to be on here crying about your lost files.

---

### Post by the-edmeister on 2010-09-27
sallam,

Sorry you had that problem with Win7 not booting, but instead of reinstalling Linux you should have asked for help here for fixing the boot loader. I had a similar problem with Windows not booting a few months ago, but I had a backup of all my valuable data on a portable hard drive. In the end I had to reinstall my OS's and programs, along with the backed up data.

My advice at this point is to install a new hard drive and install Win7. Then get a USB hard drive enclosure and see if you can recover your personal data files.

---

### Post by sallam on 2010-09-27
Thanks for all your help. I've managed to get back a few things.

---

### Post by 0N3 on 2010-09-27
Put in your windows 7 installation disk and boot from the disk and fill in your details then you come to a screen gives you option to repair your pc select this next window theres a CMD (command prompt) option select this and cmd opens up type in there bootrec.exe/fixmbr

---

### Post by sallam on 2010-09-27
> **0N3 said:**
> Put in your windows 7 installation disk and boot from the disk and fill in your details then you come to a screen gives you option to repair your pc select this next window theres a CMD (command prompt) option select this and cmd opens up type in there bootrec.exe/fixmbr

Thanks. Are those instructions meant to repair ubuntu boot loader?
I mean, what are those steps for? to be able to dual boot properly, and manage to boot into windows from the ubuntu boot loader?

---

### Post by presence1960 on 2010-09-27
> **0N3 said:**
> Put in your windows 7 installation disk and boot from the disk and fill in your details then you come to a screen gives you option to repair your pc select this next window theres a CMD (command prompt) option select this and cmd opens up type in there bootrec.exe/fixmbr

See this from earlier post from the OP:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aafef

Device Boot Start End Blocks Id System
/dev/sda1 * 1 14212 114149376 83 Linux
/dev/sda2 14212 14594 3068929 5 Extended
/dev/sda5 14212 14594 3068928 82 Linux swap / Solaris 
```

There is no windows partition on the hard disk. So why are you trying to use bootrec.exe to fix a boot loader on a non-existant windows system? The reason win 7 will not boot is because it was wiped off the disk!

---

