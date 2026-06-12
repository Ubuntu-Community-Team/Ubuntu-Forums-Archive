---
title: "How can I uninstall Ubuntu?"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Novideus on 2010-10-13
A few days ago, I read a tutorial on how to dual boot Vista and Ubuntu by partitioning the harddrive with Windows. It was a little outdated (mainly the Ubuntu setup, which was from a previous version), but I followed it as closely as I could and everything went great. However, I soon found out that my wireless adapter (Linksys WUSB100) was not compatible with Ubuntu. I have no use for an OS that I can't go on the internet with, so I'd like to safely remove Ubuntu. Please tell me how. :)

Thanks in advance!
-- Novideus

---

### Post by fatality_uk on 2010-10-13
How did you install it? Did you ran a program called Wubi to install inside windows or another way. If you post a link to the page you found to install would be helpful and then we can get it off.

---

### Post by jtarin on 2010-10-13
[Where there is a will there is a way.]("http://www.pclinuxos.com/forum/index.php?topic=68310.15;wap2")

---

### Post by Novideus on 2010-10-13
Basically I partitioned my harddrive using the windows disk management, then burned the Ubuntu .iso to a CD and rebooted with said CD in the drive. The rest was just following the prompts the Ubuntu gave me (select language/timezone/etc). 

I got the tutorial from a friend who I haven't seen in about a week (I've really procrastinated this uninstall) and I've since cleared my firefox history and never bookmarked the page. :(

I'll gladly give anymore info that I can, thanks for the quick response! :)

EDIT: Also, to jtarin, that seems pretty complicated, and I've never used any form of Linux in my life. While eventually I'd like to be able to do stuff like that without scratching my head in confusion, I think I'll need to start off a bit more slowly. For now I'll probably just go back to Windows XP, but eventually I'll get a new wireless adapter.

---

### Post by garvinrick4 on 2010-10-13
You can never work on a partition that is mounted (in use)

Boot into Ubuntu Live Cd (install Cd and use Try Ubuntu) 
  Go to System/Admin/gparted 
open gparted: right click on ubuntu partition and delete. Must click on green arrow to apply.
right click on empty ubuntu partition and format to NTFS. click on green arrow to apply.
Right click on Windows partition and choose resize and resize to use your whole drive.
If you have trouble booting back into Windows because Ubuntu took over your grub.
If you have disk use this:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
If you do not have Windows disk use Ubuntu Live Cd (install disk and choose try ubuntu)
Open a terminal: Applications/Accessories/terminal
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```May show some errors ignore we just need mbr
Reboot into Hard drive and Windows will boot.

---

### Post by azertyh on 2010-10-13
hello,
have a look at this [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by Novideus on 2010-11-24
> **azertyh said:**
> hello,
have a look at this [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

I've finally stopped dragging my feet and am ready to finally do this. I'm trying this fix, but I have a question, and I figure it's better to necro my own thread than someone else's from 2007.

So, from that thread:
> **anewguy said:**
> *PLEASE NOTE*  The above assumes your boot device is device 0

What does this mean, and how do I determine if my boot device is indeed 0, or what my boot device is at all?

Thanks in advance.
-- Novideus

---

### Post by wilee-nilee on 2010-11-24
n

---

### Post by 3rdalbum on 2010-11-24
See comment #15 from this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350695](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350695)

Just because your wifi device doesn't work out-of-the-box, doesn't mean that it won't work with Ubuntu. Alternatively, you could find one that DOES work out-of-the-box, they're pretty cheap these days.

---

### Post by hhh on 2010-11-24
> **Novideus said:**
> What does this mean, and how do I determine if my boot device is indeed 0, or what my boot device is at all?
Ugh, nobody is actually answering your questions, are they? Ignore those instructions. Your boot device is probably sda or hda, without any number after it, but you don't need to know that with my instructions.

Anyway, for XP, here's my advice. Burn the Super Grub Disk iso...
[http://www.supergrubdisk.org/super-grub-disk/](http://www.supergrubdisk.org/super-grub-disk/)

Use it to restore the Windows MBR (Master Boot Record). It's self explanatory, but if not I'll try and walk you through by memory. Choose Windows>Restore Windows MBR>Windows XP (it's either that or Boot>Tools>Restore Windows MBR>Windows XP). You should get something like "MBR restore successful!!!" Then back up through the menu prompts until you get to the one with the "Quit" option, and quit. Make sure Windows boots normally. If all is good, boot up the Ubuntu Live CD and use Gparted (under System>Administration) to delete the Ubuntu and swap partitions, they'll be the ones that are NOT labeled "ntfs" under "File System". Then extend the Windows partition. Boot into Windows, you'll be prompted to do a disc check. DO IT!!! Then continue to boot into Windows. Done.

In the future, play around with Live CDs to see if your hardware will work with the new operating system. That's what the Live CD is for.

Hope that helps.

---

