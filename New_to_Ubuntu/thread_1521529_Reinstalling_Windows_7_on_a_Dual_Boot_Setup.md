---
title: "Reinstalling Windows 7 on a Dual Boot Setup"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by SKhan on 2010-06-30
Hey Guys! I have dual boot (windows 7 + Ubuntu 10.04) and i am having countless troubles for about a week, a few minor ones with ubuntu which i will discuss some days later.
But right now i have serious problems with windows 7 and it seems that my windows 7 has just got corrupted. I am going to reinstall windows 7 from the scratch.
My questions are:
1. Will reinstalling windows 7 effect "gnu grub" and will it keep me from logging in to ubuntu?
2. if yes what i will have to do to access ubuntu once again?
3. is there a way to back up gnu grub?
4. will i be able to restore gnu grub from with in windows 7?
5. Any other precautions? since i can't afford to lose my Ubuntu installation.

---

### Post by drdos2006 on 2010-06-30
Before you reinstall Windows7, backup all your data via Ubuntu first.
My setup is 4 partitions, 1 Windows 7, 2 Ubuntu 9.10, 3 NTFS data, 4 Ubuntu swap.
Partition 3 is so that both Windows and Ubuntu can read and write to my NTFS partition.  
Install Windows 7 first as Windows 7 takes control of boot partition and anything else it can lay claim to. Ubuntu does not care which partition it is installed onto and sees Windows 7 as another operating system. Install Ubuntu second on its own partition. Then  GRUB will offer you a choice of operating systems via the boot up menu.

regards

---

### Post by wilee-nilee on 2010-06-30
First never do any of this without having backups. But if you still have to reinstall W7, just delete the main OS partition and make a new ntfs with gparted and install into it. You can also just from the live W7 run the DVD and overwrite the corrupted one and it will save the old W7 as a old windows file in the new install.

I have reinstalled W7 twice without building the ntfs to install to and both times Ubuntu became un-allocated, but when I build the ntfs ahead of I have had no problems. You will have to reinstall grub2 after here is a link to do so.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by SKhan on 2010-07-01
> **drdos2006 said:**
> Before you reinstall Windows7, backup all your data via Ubuntu first.
My setup is 4 partitions, 1 Windows 7, 2 Ubuntu 9.10, 3 NTFS data, 4 Ubuntu swap.
Partition 3 is so that both Windows and Ubuntu can read and write to my NTFS partition.  
Install Windows 7 first as Windows 7 takes control of boot partition and anything else it can lay claim to. Ubuntu does not care which partition it is installed onto and sees Windows 7 as another operating system. Install Ubuntu second on its own partition. Then  GRUB will offer you a choice of operating systems via the boot up menu.

regards
i already have a backup.
i have 6 partitions. One for windows 7, One for Ubuntu 10.04,  One for Swap, 3 NTFS data.
I am just going to format C drive and reinstall fresh copy of windows 7. Will do nothing with ntfs data partitions, ubuntu partition and swap partition.
you told me how to setup a dual boot which i already have setup for about 4 months.
my question is not even related to installing OS. It's related to REinstalling.
Either you didn't get my question or i couldn't get your answer.:p

---

### Post by SKhan on 2010-07-01
> **wilee-nilee said:**
> First never do any of this without having backups. But if you still have to reinstall W7, just delete the main OS partition and make a new ntfs with gparted and install into it. You can also just from the live W7 run the DVD and overwrite the corrupted one and it will save the old W7 as a old windows file in the new install.

I have reinstalled W7 twice without building the ntfs to install to and both times Ubuntu became un-allocated, but when I build the ntfs ahead of I have had no problems. You will have to reinstall grub2 after here is a link to do so.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

well i am quite expert in windows feild, and installing reinstalling windows is nothing new to me.
but this time it's different just because it's the first time i am going to reinstall windows over dual boot with ubuntu. So any precautions i asked for were specific to GRUB thing. I just want GRUB back after reinstalling windows 7.
I am going to check out the link you gave.

---

### Post by SKhan on 2010-07-01
sorry bro. that link is to detailed and too technical for me to understand.

no body answered my simple questions.

that are:

1. is there a way to backup GRUB before procedeeing to reinstall windows 7?
2. is there a way to restore grub JUST WITH THAT BACKUP from WITHIN WINDOWS?

guys please have pity on me, i am having seriously hard time. i can't proceed to reinstall windows unless i first get the solution to get my grub back. And i just can't afford to lose my ubuntu installation.
i have to come to my friend's place in order to post here. can't connect from my system because windows is just got corrupt. and my isp changed net settings, now they are telling me to create a pppoe connection and i don't know how to do that in ubuntu. so right now i can't connect to internet from my own computer.
a lot of other problems also exist, so please have some pity and answer my question clearly and as soon as possible. please.

---

### Post by wilee-nilee on 2010-07-01
> no body answered my simple questions.

that are:

1. is there a way to backup GRUB before procedeeing to reinstall windows 7?
2. is there a way to restore grub JUST WITH THAT BACKUP from WITHIN WINDOWS?

guys please have pity on me, i am having seriously hard time. i can't proceed to reinstall windows unless i first get the solution to get my grub back. And i just can't afford to lose my ubuntu installation.
i have to come to my friend's place in order to post here. can't connect from my system because windows is just got corrupt. and my isp changed net settings, now they are telling me to create a pppoe connection and i don't know how to do that in ubuntu. so right now i can't connect to internet from my own computer.
a lot of other problems also exist, so please have some pity and answer my question clearly and as soon as possible. please.



The link defaults to the Process #11 how to install grub2 using a live cd if you follow it you should have no problems, this is a standard method.

If you haven't done this before I can understand your intrepidation.

All that has to done is to reload the grub2 bootloader back into the MBR. I think what you don't realize is that there are grub.cfg files in Ubuntu like the boot files inside of Widows the bootloader works with these to boot. If you could save the MBR information it wouldn't matter anyway as chances are the new W7 label=UUID would be different probably.

Your questions were answered in the Linux/Ubuntu way of doing things.

No you can't restore grub from windows.

---

### Post by SKhan on 2010-07-02
> **wilee-nilee said:**
> The link defaults to the Process #11 how to install grub2 using a live cd if you follow it you should have no problems, this is a standard method.

If you haven't done this before I can understand your intrepidation.

All that has to done is to reload the grub2 bootloader back into the MBR. I think what you don't realize is that there are grub.cfg files in Ubuntu like the boot files inside of Widows the bootloader works with these to boot. If you could save the MBR information it wouldn't matter anyway as chances are the new W7 label=UUID would be different probably.

Your questions were answered in the Linux/Ubuntu way of doing things.

No you can't restore grub from windows.

ok let me read process #11. thanks for your co-operation. :)

---

### Post by SKhan on 2010-07-05
> **wilee-nilee said:**
> The link defaults to the Process #11 how to install grub2 using a live cd if you follow it you should have no problems, this is a standard method.

If you haven't done this before I can understand your intrepidation.

All that has to done is to reload the grub2 bootloader back into the MBR. I think what you don't realize is that there are grub.cfg files in Ubuntu like the boot files inside of Widows the bootloader works with these to boot. If you could save the MBR information it wouldn't matter anyway as chances are the new W7 label=UUID would be different probably.

Your questions were answered in the Linux/Ubuntu way of doing things.

No you can't restore grub from windows.
i have understood it. Will try in a couple of day.

---

### Post by SKhan on 2010-07-05
Thanks a lot man i have just re-installed windows 7 and got GRUB back from live CD. It worked like a charm. Thank you for such a great help. Me so happy. :-({|=

---

