---
title: "Triple Booting"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by Solstice Bahai on 2011-05-07
High guys, Sorry to be a pain, but I think I have gone and done something stupid, perhaps VERY stupid.:( I decided to go the distance and dual boot my Acer Aspire5740, Long story short, I looked at a distro via Live cd ( Trisquel, and liked what I saw, and INSTALLED it, but found that while it saw my wireless, it would'nt allow me to go online, even though it said I had 100% CONNECTION!! The browser kept saying problem loading page and not finding server so I can't update the packages or anything:confused: Then while I was idly browsing(via Win7) Ubuntu website, I installed Ubuntu via Wubi downloader. But it wont let me connect to the web via either the usb dongle ( a Huawei1550 3G mobile broadband dongle, keeps telling me GSM Disconnected) or via the wireless modem dongle ( a Huawei E5830 WiFi dongle) which times out and repeats asking for my WiFi Key password. What do I do??? I dont know how to remove Trisquel ( and keep Ubuntu....and yes Win7 ) on this machine WITHOUT doing a full format and re- installing Win7 and Ubuntu(via Wubi):(

---

### Post by Thewhistlingwind on 2011-05-07
Gparted/etc. Use a partition editor, destroy the unwanted partition and then resize the other two to fill it's space.

Warning: You can mess your system up far (FAR!) worse by attempting this. If you don't NEED the 3rd OS gone, don't bother. 

It would be a very good idea to backup if you have the space before trying the above advice.

EDIT: Also, I'm not sure if that will work, FYI.

---

### Post by Solstice Bahai on 2011-05-07
Thanks for the advice, I have too much respect for my own ignorance  to try some thing like that, without some understanding of what is involved. It does not seem to have affected the laptop itself much, Trisquel looks really cool, and if the connection issues were resolved I would definetly use it. As for Ubuntu which I installed via Wubi, that does ok as well, just got to get going online, and I LOVE  Natty!! as I have it as the ONLY OS on my netbook. and It does look beautiful on this larger Notebook.> The Earth is but One Country, and Mankind its Citizens

---

### Post by Lateralis on 2011-05-07
First question: What bootloader do you get when you start the computer?  Do you get a version of Grub (grub legacy or version 2?) or do you get the Windows bootloader?  If you get Windows then that actually simplifies things a bit.  

Secondly, I strongly recommend with every single fibre of my being, to use the Windows 7 tools if you want to expand or shrink a Windows partition.  NTFS support in Linux is OK but not entirely foolproof and you may end up with data loss if you shrink an NTFS using GParted.  Also, Windows does not generally approve of its (system) partition(s) being fondled by anything other than the Windows tools.  

So, if you have the Windows bootloader, simply boot into Windows and use the Win tools to nuke the other Linux distro and expand the Windows partition(s) as you see fit.  If you want rid of both Ubuntu Wubi and the other linux distro... First nuke the first distro then you can uninstall the Ubuntu Wubi in Windows, as Ubuntu is installed like a program.  As such, it can be uninstalled, like any other program.  

If you have the Grub bootloader, then the above steps are valid but I would recommend first isntalling the Windows bootloader over the top of Grub.  This will mean you cannot boot into the Linux distros, but does mean you can do anything to those distros without being unable to boot.  This is because Grub looks for boot files within the Linux partition in order to give you the boot menu.  Without those files it can't and will give an error.  

One final, quite obvious comment... before you do anything to anything, ensure that all of your important data is backed up to an external medium, such as CDs, DVDs or an external hard drive.  The chances of something going wrong are slim, but when they do it can be disastrous, heart breaking or both.

---

### Post by Solstice Bahai on 2011-05-07
> **Lateralis said:**
> First question: What bootloader do you get when you start the computer?  Do you get a version of Grub (grub legacy or version 2?) or do you get the Windows bootloader?  If you get Windows then that actually simplifies things a bit.  

Secondly, I strongly recommend with every single fibre of my being, to use the Windows 7 tools if you want to expand or shrink a Windows partition.  NTFS support in Linux is OK but not entirely foolproof and you may end up with data loss if you shrink an NTFS using GParted.  Also, Windows does not generally approve of its (system) partition(s) being fondled by anything other than the Windows tools.  

So, if you have the Windows bootloader, simply boot into Windows and use the Win tools to nuke the other Linux distro and expand the Windows partition(s) as you see fit.  If you want rid of both Ubuntu Wubi and the other linux distro... First nuke the first distro then you can uninstall the Ubuntu Wubi in Windows, as Ubuntu is installed like a program.  As such, it can be uninstalled, like any other program.  

If you have the Grub bootloader, then the above steps are valid but I would recommend first isntalling the Windows bootloader over the top of Grub.  This will mean you cannot boot into the Linux distros, but does mean you can do anything to those distros without being unable to boot.  This is because Grub looks for boot files within the Linux partition in order to give you the boot menu.  Without those files it can't and will give an error.  

One final, quite obvious comment... before you do anything to anything, ensure that all of your important data is backed up to an external medium, such as CDs, DVDs or an external hard drive.  The chances of something going wrong are slim, but when they do it can be disastrous, heart breaking or both.
Well it seems that it boots into some form of the Grub boot loader, because when it boots up I am presented with a rough screen and three choices...1st is Trisquel then Vista something dev then Windows7 something dev.
When I choose the Win7 option I get the normal duel boot menu, Win7 or Ubuntu

---

### Post by Solstice Bahai on 2011-05-07
:confused:> **Lateralis said:**
> First question: What bootloader do you get when you start the computer?  Do you get a version of Grub (grub legacy or version 2?) or do you get the Windows bootloader?  If you get Windows then that actually simplifies things a bit.  

Secondly, I strongly recommend with every single fibre of my being, to use the Windows 7 tools if you want to expand or shrink a Windows partition.  NTFS support in Linux is OK but not entirely foolproof and you may end up with data loss if you shrink an NTFS using GParted.  Also, Windows does not generally approve of its (system) partition(s) being fondled by anything other than the Windows tools.  

So, if you have the Windows bootloader, simply boot into Windows and use the Win tools to nuke the other Linux distro and expand the Windows partition(s) as you see fit.  If you want rid of both Ubuntu Wubi and the other linux distro... First nuke the first distro then you can uninstall the Ubuntu Wubi in Windows, as Ubuntu is installed like a program.  As such, it can be uninstalled, like any other program.  

If you have the Grub bootloader, then the above steps are valid but I would recommend first isntalling the Windows bootloader over the top of Grub.  This will mean you cannot boot into the Linux distros, but does mean you can do anything to those distros without being unable to boot.  This is because Grub looks for boot files within the Linux partition in order to give you the boot menu.  Without those files it can't and will give an error.  

One final, quite obvious comment... before you do anything to anything, ensure that all of your important data is backed up to an external medium, such as CDs, DVDs or an external hard drive.  The chances of something going wrong are slim, but when they do it can be disastrous, heart breaking or both.
Well it seems that it boots into some form of the Grub boot loader, because when it boots up I am presented with a rough screen and three choices...1st is Trisquel then Vista something dev then Windows7 something dev.
When I choose the Win7 option I get the normal duel boot menu, Win7 or Ubuntu

---

### Post by Solstice Bahai on 2011-05-07
Hi guys,sorry to report that I did make a complete ****-up of things on the Acer Aspire 5740.]:confused:I looked at the windows tools as suggested, and I will be brutally honest, I had not a clue as to what they do or mean to do.Like a lot of people,I am as much a MORON regarding computers as I am a newbie to Linux.So in the end I tried a recovery of Windows,which got rid of the Ubuntu (I really wanted to keep!!) which had been installed under Wubi in Windows. As the Trisquel Distro, It did NOTHING to remove it.I was left with a Distro I did not want and broken Windows install. I got rid of the Trisquel by doing a COMPLETE install from a live cd (Open Suse)
 Which I got rid of by installing ANOTHER distro,UBUNTU 9.04 64Bit.
I am writing this on the Samsung N150 netbook, because on ther machine Ubuntu"sees"my wireless... but for some reason will not connect! I get page load errors and failing to find servers messages on the screen ( firefox page). If any other person reading this is as new as I am...LET THIS BE AN ABJECT LESSON!! Don't mess with what you what you fully know or understand.
I am however not giving up!! I WILL get to grips with Linux and computers and have something I can call a skill and an achievement:(

---

### Post by robgraves on 2011-05-07
WOW :shock:, so what is the current setup on the computer in question?

---

### Post by Solstice Bahai on 2011-05-07
Current set-up on Laptop in question is that it runs Ubuntu 9.04 but without fancy graphics ( says machine is not capable,so has dis-abled, but the Acer Aspire 5740 has Blueray for pete's sake, and uses an on-board intel graphics media accelerator, also no blue tooth) and no internet as in Can't get it working!! Apart from that, every thing else seems to be ok, At least my notebook is alive with an OS

---

### Post by Solstice Bahai on 2011-05-07
I am however going to be taking round to a friend who has a wired broadband, and I will humbly request to use it so I can get said laptop up to spec with Natty! and hope fully solve its wireless probs at the same time

---

### Post by robgraves on 2011-05-08
is ubuntu 9.04 the only OS on it or do you still have windows on it?

---

### Post by Solstice Bahai on 2011-05-08
> **robgraves said:**
> is ubuntu 9.04 the only OS on it or do you still have windows on it?
The only, sorry for taking so long in replying, but I had to take a rest,this whole thing really shattered me

---

