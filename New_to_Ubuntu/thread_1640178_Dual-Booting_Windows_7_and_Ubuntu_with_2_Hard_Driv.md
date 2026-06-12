---
title: "Dual-Booting Windows 7 and Ubuntu with 2 Hard Drives"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by Sturmdolch on 2010-12-07
Hello,

I've been searching on Google for the last while and can't seem to find much that fits what I have in mind.

I am mainly a Windows user, but I want to use Ubuntu for programming, homework, and other things. I have never used Ubuntu before, and my only experience with Linux is our school computers that run an old version of XFCE. 

I just bought a new computer and I have two 1TB hard drives. 

On hard drive 1, I want Windows 7 64-bit and whatever programs and data I need for it.

On hard drive 2, I want two partitions, 300GB for Ubuntu 64-bit and 700GB for shared data.

When I boot up my computer, I want it to automatically boot up Windows 7 unless I choose to boot Ubuntu. Preferably in a menu that pops up and gives me five seconds to make a selection, as I've read GRUB does.

From which OS installation do I partition the second drive?
Will I be able to access the data partition from Windows 7 and Ubuntu?
Will I be able to give Windows 7 the priority in boot order for GRUB?
Will I lose any performance by using GRUB over manually switching hard drives in the BIOS?

Thank-you very much!

---

### Post by amjjawad on 2010-12-07
Hello and welcome :)

> **Sturmdolch said:**
> From which OS installation do I partition the second drive?

From Ubuntu's LiveCD. Use GParted ( System > Administration > GParted)

> Will I be able to access the data partition from Windows 7 and Ubuntu?
Your best option is to format that data partition as NTFS. In my opinion, 700GB is way too much but that's only me.

> Will I be able to give Windows 7 the priority in boot order for GRUB?
Yes, I think you can.

> Will I lose any performance by using GRUB over manually switching hard drives in the BIOS?I'm afraid I didn't understand that?
However, GRUB2 is a very powerful Boot Manager and has lots of nice features. It's my favorite.

---

### Post by oldfred on 2010-12-07
Use windows tools for windows and use Linux tools for Linux is the safest way, but sometimes you have to use Linux to fix Windows:).

The latest installer only gives you a choice on where to install grub, Ubuntu's boot loader if you use manual install. You will want grub installed to the MBR of sdb the Ubuntu drive, not sda the windows drive, but it usually defaults to sda. Once installed to sdb you set BIOS to boot sdb and you can set windows as the first to boot if you want. Some suggest physically disconnecting the windows drive to avoid any issue of grub installing to the wrong drive's MBR.

I always use gparted either from liveCD or a separate download of a gparted liveCD to create partitions and then use manual install to format and choose which partition is / (root), and /home. If swap created in advance it auto finds it.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)
Full Disk Install
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat](http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by Jerry N on 2010-12-07
Disconnect your Windows drive and install Ubuntu on the second drive.  Make sure Ubuntu works the way you want it then power down and re-connect the Windows drive.  Reboot the computer and Ubuntu should restart with a boot screen giving you the option of starting Ubuntu (default) or Windows.  At this point, you have made no changes to the Windows drive.  You can then use the boot manager in Ubuntu to select which OS is default.  Alternatively, reset the boot drive order in the BIOS so that Windows boots first and select the Ubuntu drive during the boot process when desired.  I use Gigabyte motherboards and hitting the F12 key a few times during the boot process will bring up the menu allowing selection of the boot device.  This is the way I do it and it has the advantage of leaving the boot sector on the Windows drive completely intact so that you could remove the drive containing Ubuntu and still be able to boot Windows.

Jerry

---

### Post by Sturmdolch on 2010-12-07
> **Jerry N said:**
> Disconnect your Windows drive and install Ubuntu on the second drive.  Make sure Ubuntu works the way you want it then power down and re-connect the Windows drive.  Reboot the computer and Ubuntu should restart with a boot screen giving you the option of starting Ubuntu (default) or Windows.  At this point, you have made no changes to the Windows drive.  You can then use the boot manager in Ubuntu to select which OS is default.  Alternatively, reset the boot drive order in the BIOS so that Windows boots first and select the Ubuntu drive during the boot process when desired.  I use Gigabyte motherboards and hitting the F12 key a few times during the boot process will bring up the menu allowing selection of the boot device.  This is the way I do it and it has the advantage of leaving the boot sector on the Windows drive completely intact so that you could remove the drive containing Ubuntu and still be able to boot Windows.

Jerry

Thanks, I'll give this a try.

Thanks for the other suggestions, too. I'll keep them all in mind when I go for it tomorrow or Thursday.

---

### Post by amjjawad on 2010-12-08
> **Sturmdolch said:**
> I'll keep them all in mind when I go for it tomorrow or Thursday.

Good luck and don't forget to tell us what happened with you :)

---

### Post by Sturmdolch on 2010-12-09
> **amjjawad said:**
> Good luck and don't forget to tell us what happened with you :)

Alright!

I looked for a while on how to partition drives to make a data partition. But it looked hard, and I don't want to mess something up by accident. So I just installed Windows 7 on one hard drive, disconnected it and installed Ubuntu on the other, then plugged them both in with priority to Ubuntu. 

Then I ran StartUp-Manager, and set Windows to default with 7 seconds to make a choice.

To be honest, though, I really like the way Ubuntu looks and acts. At first I was a little dismayed that I couldn't open the terminal in a place I right click on, but it turns out that "there's a[s]n app[/s] command for that. I'm surprised at how much I like it. I definitely see myself using Ubuntu for programming and casual use, while Windows serves me for games and Office.

Thanks for the help! Much appreciated.

---

### Post by amjjawad on 2010-12-09
So everything is fine, right?
If you don't have any more questions, please mark this thread as "SOLVED" so it would help others for future reference :)

Glad you managed to get it up and running and hope you'll enjoy Ubuntu :)

---

