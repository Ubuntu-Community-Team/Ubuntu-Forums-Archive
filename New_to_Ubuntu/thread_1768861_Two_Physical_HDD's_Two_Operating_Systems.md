---
title: "Two Physical HDD's Two Operating Systems"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by OwainGlyndwr on 2011-05-27
Hi again,

after a lot of teeth gnashing and sleepless nights.  :D

I would like to try Ubuntu 11.04 again.

But this time install it to my 2nd HDD, while retaining Win 7 on my main HDD.

Is this possible and will it be a dual bootable configuration.

Could i also ask, is there an idiots guide to installing third party software into Ubuntu.

I understand from my last brief encounter, that it is a very different proceedure to "click and install" in Windows.  ;)

cheers,
Mike.

---

### Post by ApOgEEs on 2011-05-27
> **OwainGlyndwr said:**
> Hi again,

after a lot of teeth gnashing and sleepless nights.  :D

I would like to try Ubuntu 11.04 again.

But this time install it to my 2nd HDD, while retaining Win 7 on my main HDD.

Is this possible and will it be a dual bootable configuration.

Could i also ask, is there an idiots guide to installing third party software into Ubuntu.

I understand from my last brief encounter, that it is a very different proceedure to "click and install" in Windows.  ;)

cheers,
Mike.

Yes, it is possible to install Ubuntu dual boot on 2nd HDD

Here is the guide to install third party software in Ubuntu: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

If you found the *.deb file, you can simply double-click and Install it in Ubuntu. I found it even easier than in Windows :)

---

### Post by oldfred on 2011-05-27
Herman has one of the few guides on installing to a second drive. Still based on Maverick, but only some screens have changed slightly, the process is the same. He has  a lot of detail but it is not as hard as it may seem because of the detail he gives.

You do want to be sure to use manual install, both so you get to choose partitions and where to install the grub2 boot loader. You want the boot loader on the same drive as the Ubuntu install and not interfere with windows. Or each drive should work if you unplugged the other drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external Maverick screens shown
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by verymadpip on 2011-05-27
I've not read the guide (my bad) & I have 11.04 & W7 each on their own HDD.
It is very doable.
I stuck GRUB on the Ubuntu drive & then set it as the first boot HDD in BIOS.
GRUB picked up W7 no problem & it all ticks over very well.

I do have to disconnect my Ubuntu HDD if I want to mess with msconfig (which I don't like or do often).

Good luck & let us know how it goes.

---

### Post by OwainGlyndwr on 2011-05-27
Thank you everyone for your help and patience.

Also many thanks for the links to the install information.

Could i just take up just a bit more of your time please guys.

To ask what is "GRUB" ?

Thanks again.

Mike.

---

### Post by wolfen69 on 2011-05-27
> **OwainGlyndwr said:**
> 
To ask what is "GRUB" ?


**GR**and **U**nified **B**ootloader

It handles the OS's on your computer so you can choose which one to boot into. 

Another way to do the install is to unplug the windows drive and install ubuntu. Then you can choose at boot up time (usually F12) which drive you want to boot. I used to do it this way when I first started.

---

### Post by ApOgEEs on 2011-05-27
> **OwainGlyndwr said:**
> 
To ask what is "GRUB" ?


**GRUB** is more than just a boot loader. It is also the world's best boot manager, meaning it is best installed to the Master Boot Record of the first hard disk. That way GRUB will be the first thing that loads when the computer starts. It allows you to boot Linux directly or boot another boot loader which can then load its own operating system(s). You can have different operating systems, and versions of them, on the same or different hard drives. For example, if you have both Windows and Linux installed on a computer, GRUB would load before either of these and let you choose which one to boot. 

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

**GRUB 2** is the default boot loader and manager for **Ubuntu since version 9.10 (Karmic Koala)**. As the computer starts, GRUB 2 either presents a menu and awaits user input or automatically transfers control to an operating system kernel. GRUB 2 is a descendant of GRUB (**GR**and **U**nified **B**ootloader). It has been completely rewritten to provide the user significantly increased flexibility and performance. GRUB 2 is Free Software. 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by OwainGlyndwr on 2011-05-29
Hi guys,

thank you for the info in regards "GRUB".

Well i must say this time it was easy. I didn't have to do a thing, i chose the second install option ( install alongside windows ).

The third option seemed to complicated, so i back tracked and re-chose the second.

It auto chose sdb and not sda this time, so i double checked that was correct.

Started the install and it went in without problems.

I have updated the video driver for my 2x Nvidia 8800GTX cards in SLI mode ( not sure if Linux supports SLI ).

What suprised me was the fact that my SoundBlaster 7.1 system, did not need any extra drivers, unlike Windows. I wacked a .flac file into Banshee and it played straight away, excellent quality as well.  :D

The thing i would really like to be able to do is play Trainz Railway Simulator, installed to Linux.

It is what i use the pc for mainly as well as the net of course.

I believe i have to install Wine to do that ?

If it will run TS12, i will dump Win 7 completely.  :)

Thank you all for replying in this thread, much appreciated.

EDIT:  The bootloader works fine, it gives me two options of Ubuntu, two memory tests i think and Win 7.

regards,
Mike.

---

### Post by wolfen69 on 2011-05-29
What version of trainz are you running? Some versions work well, others not so much. The only way to know is to try. Also, to give you an idea about trainz in wine: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1468](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1468)

---

### Post by ApOgEEs on 2011-05-29
Hi Mike,

Good to hear your experience with your newly installed Ubuntu. It seems that you have solved your "Two Physical HDD's Two Operating Systems" issue. So, please mark this post as [SOLVED]. 

Here is the tutorial on **[How to mark thread [SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")**

Thank you.

---

### Post by OwainGlyndwr on 2011-05-30
Thank you wolfen69, i am running the latest ( TS12 ). Looks like it doesn't do so well.  :(

ApOgEEs,

yup problem solved thanks to the great help i got here.  :)

Best regards,
Mike.

---

### Post by grahammechanical on 2011-05-30
Hi

I am glad that things have worked out well for you. Yes, there has been a big improvement, especially with Ubuntu, over the last few years. May I recommend that you install Grub Customizer?

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

I also think that the Ubuntu Software Centre is a big improvement in the installation of programs and applications.

Regards.

---

### Post by OwainGlyndwr on 2011-05-30
Hi Graham,

thank you for the link, but i better leave well alone i think.  :)

I have another problem now, which i won't go into here, as it is unrelated to my original question.  ;)

Many thanks,
Mike.

---

### Post by OwainGlyndwr on 2011-05-31
Just to wind this up, i installed Trainz Sim 12.

The front end launches and the Content Manager works.

But the main game will not, i just get a big message about directx, video drivers etc etc.  :(

cheers,
Mike.

---

