---
title: "Boot time problem. Afraid to install Ubuntu !"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by luckydeveloper on 2010-01-03
Hi,

I have been using ubuntu alongside windows for many of these years right from 6.06 days. 

I installed ubuntu via Wubi. So the computer should boot and screen should show me the Boot options (Windows/ubuntu).Am i right ??

For the past 2 months, I have been facing this problem. 
When i boot, the first screen (lenovo screen ) comes up (usual) and the LCD screen goes black. The boot loader options are not shown, instead it just stays dark for a few mins and boots the default OS (Windows) directly. And then I get the windows logon screen directly.Not even the windows XP booting screen comes up. Till then the screen stays dark. 

I uninstalled ubuntu and I no longer get the problem. I can see the windows XP booting screen now. Only when i install ubuntu, i get this problem i guess. what may be the problem. I am afraid to install ubuntu and am afraid whether it will do some harm to my system. please help

I want to use ubuntu but cannot afford to spend any money if it does any harm to my system. I want this problem to get solved. Please do help.

---

### Post by kyuubi777 on 2010-01-03
hey, I have a lenovo laptop as well. I used to dual boot with xp and 9.04 and then 9.10 and 7 (both worked perfectly). but i got sick of windows so I axed it... you can go through the live cd to reinstall only the grub boot loader which seems to have broken on your machine (i speculate that some file or other is broken on your windows side as well, so you might have to reinstall windows as well)
i have found though, that the easiest method is to divide your hdd into 4 partitions, one for swap space..a windows ntfs partition and then two other partitions for operating systems (same size) and install ubuntu on one of them. then, if you experience issues you can simply install ubuntu on the unused partition and mount the original file system and drag the files over to the new operating system... and then use the old ubuntu partition for reserve space to do that same thing in case of another error.

---

### Post by wirate on 2010-01-03
Thats a strange problem. Wubi cannot, AFAIK, do any serious damge to your system. Even if it does, you can run "fixmbr" booting into the recovery console from your Windows cd. If you are still afraid, you can install ubuntu on a different hdd.

---

### Post by Temposs on 2010-01-03
You should not install via Wubi if you are serious about using Ubuntu. You should install in the standard fashion. This may work better for you than Wubi. First, you should make a LiveCD and test-run Ubuntu with that before you install, to make sure it boots up and basic things like internet and sound work.

Of course, back up your important files before you install.

---

### Post by kyuubi777 on 2010-01-03
i've never used wubi or bothered to read about it.. i figured it installed ubuntu completely on a new partition as if doing it through a live cd only that it's done through windows... sorry if i am wrong and i just confused op even more

---

### Post by luckydeveloper on 2010-01-03
> **kyuubi777 said:**
> hey, I have a lenovo laptop as well. I used to dual boot with xp and 9.04 and then 9.10 and 7 (both worked perfectly). but i got sick of windows so I axed it... you can go through the live cd to reinstall only the grub boot loader which seems to have broken on your machine (i speculate that some file or other is broken on your windows side as well, so you might have to reinstall windows as well)
i have found though, that the easiest method is to divide your hdd into 4 partitions, one for swap space..a windows ntfs partition and then two other partitions for operating systems (same size) and install ubuntu on one of them. then, if you experience issues you can simply install ubuntu on the unused partition and mount the original file system and drag the files over to the new operating system... and then use the old ubuntu partition for reserve space to do that same thing in case of another error.

My system is facing problems when i dont install ubuntu with wubi. 
When i install it directly as you say, windows partition is not working and Ubuntu is working. When i choose windows in the boot loader, i get some boot error and windows does not boot. 

But when i install it with wubi, that problem is not occuring. That is why i choose wubi to be my installer, then windows loads perfectly. If you know any solution for this problem, please propose it.

---

### Post by luckydeveloper on 2010-01-03
> **Temposs said:**
> You should not install via Wubi if you are serious about using Ubuntu. You should install in the standard fashion. This may work better for you than Wubi. First, you should make a LiveCD and test-run Ubuntu with that before you install, to make sure it boots up and basic things like internet and sound work.

Of course, back up your important files before you install.

I am serious about using ubuntu. But i need windows too for my college project work. 

Windows does not boot when i install ubuntu in the standard fashion. When i choose windows in the boot time ( when i install ubuntu in standard fashion), I get some error 18 or 21 i dont remember the error number.

---

### Post by Temposs on 2010-01-03
> **kyuubi777 said:**
> i've never used wubi or bothered to read about it.. i figured it installed ubuntu completely on a new partition as if doing it through a live cd only that it's done through windows... sorry if i am wrong and i just confused op even more

Wubi installs Ubuntu as a file within Windows. It does not create a new partition at all. So it is quite different from a normal install as it concerns the global filesystem.

---

### Post by kyuubi777 on 2010-01-03
ahhhhh i think i get it.. it's almost parring on emulation at that point then right?.. if you have to access it through an ntfs filesystem

and best bet will be for op to partition and reinstall windows first and then ubuntu... straight install both from scratch and you shouldn't have any issues.. i'd also recommend using 9.04 instead of 9.10.. it'll run a lot more stable and all you really sacrifice is slightly better graphics in 9.10 and wifi connectivity on boot

---

### Post by la3875 on 2010-01-03
I reccomend you take the advice from the earlier posts to repair your Windows installation and then use a live disc to install Ubuntu - letting it create its own partition, etc. I have been using successfully since 5.10, including removal and reinstallation and fixing Windows MBR via instructions here - [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Cheers!

---

### Post by Temposs on 2010-01-03
> **luckydeveloper said:**
> I am serious about using ubuntu. But i need windows too for my college project work. 

Windows does not boot when i install ubuntu in the standard fashion. When i choose windows in the boot time ( when i install ubuntu in standard fashion), I get some error 18 or 21 i dont remember the error number.

I understand you need Windows for some things. That is understandable. I think sorting out that boot error would be the ideal way to solve your problem. So it was grub error 18 you were getting?

---

### Post by luckydeveloper on 2010-01-03
> **Temposs said:**
> I understand you need Windows for some things. That is understandable. I think sorting out that boot error would be the ideal way to solve your problem. So it was grub error 18 you were getting?

yes, it was grub error 18 that came last time i installed ubuntu in the standard fashion.

If i install ubuntu in standard fashion, Ubuntu would work but not windows. And I get Error 18.Thats the problem

---

### Post by Temposs on 2010-01-03
After looking at some forum posts that seem related to your problem, it seems a bit bothersome. But, if you want to look into it, you might check here:

[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)
[http://bbs.archlinux.org/viewtopic.php?id=64107](http://bbs.archlinux.org/viewtopic.php?id=64107)

If you don't want to mess with all that, have you considered using Virtualbox for your Windows needs? That's what I use. Unless you need Windows to play high-end 3D games or to do very heavy processing, it is adequate for doing needed work within Windows. I do some development with Microsoft Visual Studio in Windows, and it works well for that.

---

### Post by Temposs on 2010-01-03
The process for using Virtualbox in Ubuntu to run Windows this way would go like this:

1) Backup your data
2) Install Ubuntu, reformatting the entire hard drive.
3) Install Virtualbox on Ubuntu
4) Install Windows on Virtualbox

You can also do the opposite, installing Ubuntu with Virtualbox on Windows.

1) Install Virtualbox on Windows
2) Install Ubuntu on Virtualbox

It depends if you want to use Ubuntu or Windows as your primary OS. I prefer Ubuntu as my primary OS, as it is free/open source, and not likely to get malware. The advantage to installing Windows within Virtualbox is that it's a sandbox, that is, it won't infect your entire sytem if it gets infected.

---

### Post by luckydeveloper on 2010-01-03
> **Temposs said:**
> The process for using Virtualbox in Ubuntu to run Windows this way would go like this:

1) Backup your data
2) Install Ubuntu, reformatting the entire hard drive.
3) Install Virtualbox on Ubuntu
4) Install Windows on Virtualbox

You can also do the opposite, installing Ubuntu with Virtualbox on Windows.

1) Install Virtualbox on Windows
2) Install Ubuntu on Virtualbox

It depends if you want to use Ubuntu or Windows as your primary OS. I prefer Ubuntu as my primary OS, as it is free/open source, and not likely to get malware. The advantage to installing Windows within Virtualbox is that it's a sandbox, that is, it won't infect your entire sytem if it gets infected.

Thank you so much mate. This is what Im gonna try now. 

1. I will format my entire system after taking some backups. Then with the help of the steps provided in the GRUB wiki, I will see whether I can install ubuntu in the normal fashion.
2. If the above does not work, I am gonna use virtual box as per your instructions, anyways i will get back to this thread with the news of my attempts. 

:) thanks again for all the support dude !!

---

