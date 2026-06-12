---
title: "Dual Boot REinstall Possible?"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by wbee on 2009-03-23
Hello,

I have XP on half my hard drive and 8.10 on the other half,with the selection made following the grub prompt. I moved the slider.

If I use the CD to reinstall 8.10,will it retain the XP and all my files and records there?

Yes,I know. Why?:-)

--1.I have lots of stuff to move.

--2. Until I figure out Linux-Debian sound, alsa and pulse and the three layers and all that stuff,I want to keep XP for some audio- video applications.

------------

Thank you

---

### Post by Cypher on 2009-03-23
Are you talking about the disk drive Slider during Ubuntu installation? If you don't make any changes to the hard drive partitions that were previously under Ubuntu control when you re-install, it will do nothing bad to your WinXP installation and you can go about your way.

If you were to slide things around, you might want to elaborate more on what you are doing so that we can tell you if that'll harm your XP installation or not.

Either way, beofre doing a re-installation, you might want to take a moment and backup your most important files on an external HD or something..

---

### Post by MttJocy on 2009-03-23
The ubuntu installer will not be able to safely resize or otherwise modify your windows partition (make sure you don't accidentally set it to format it either) Doing any of these will erase the windows partition. (Note: Based on last install of 8.10 this may not be the case with 9.04 someone else would need to say if anyone was using that)

However if you only modify the partitions which originally held ubuntu and leave the windows partition well alone in the partitioner (except to check the format check box is cleared) you should be fine. Although as always when making a fairly drastic change to the system installation backing up your most critical files and data would be strongly recommended errors can and do sometimes happen.

But as the other guy said if you tell us exactly what you are looking to do we can say for sure.

---

### Post by wbee on 2009-03-23
Cypher and MttJocy,

Yes. When I installed,I moved the horizontal slider to allot half the drive to XP and half the drive to 8.10.

So,you're telling me if I simply choose the dual boot option,and don't touch the slider,that it should work?

----------

Thanks.

---

### Post by gn2 on 2009-03-23
Doing anything that alters any partition in any way is not without risk.

Which is why you should get into the good habit of **always** making sure you have a good back-up on removable media of all the files you need to keep **before** you start changing pertitions.

---

### Post by aikiwolfie on 2009-03-23
When you get to the partitioning part, select the option to use your own custom partition setup. This will take you to a screen showing the current arrangement on your hard disc. Simply select your Ubuntu partition and take it from there.

Remember just take your time and read everything carefully before committing to anything.

May I ask why your reinstalling Ubuntu? Is it simply the case grub got mangled or something?

---

### Post by wbee on 2009-03-23
aikiwolfie,

I have Nvidia on board video hardware on my MSI motherboard. 8.10 prompted me to download and install a proprietary driver.

I did. Ever since then,I have had screen resolution and screen speed issues. When I reported it to lauchpad,I saw that many others are having issues with those drivers.

So,I figure to reinstall and wait for the "issue resolved" notice before downloading it again.

The grub works perfectly.

---------

Thanks.

---

### Post by aikiwolfie on 2009-03-23
You should be able to simply disable the proprietary NVIDIA driver if it's causing a problem. If you can get logged in to the desktop check "System > Administration > Hardware Drivers". You should be able to disable it from there.

---

### Post by wbee on 2009-03-23
aikiwolfie,

Thanks again. :-) 

Yes,I can get in.

What I'm going to try is to use the "Envy" software to clean it up,have Envy reinstall it,(in case the bug is in the installer function),and if that works,fine.

If not,I can always uninstall it again.

PS. It is good to know that I can keep the partitions if the need ever arises to reinstall.

---

### Post by aikiwolfie on 2009-03-23
No problem :) Happy to help.

---

