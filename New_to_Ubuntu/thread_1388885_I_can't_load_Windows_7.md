---
title: "I can't load Windows 7?"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by CommanderTux64 on 2010-01-23
OK! i installed Ubuntu 9.10 and i kept Windows 7 when i boot up my computer it goes to GRUB and i picked Windows 7 it loaded right after it did it flashed and it rebooted how do i go back to windows 7 i want to have two OSes (operating systems) without having to keep Ubuntu forever please help my dad will kill me:confused:

---

### Post by CommanderTux64 on 2010-01-23
I just installed Ubuntu 9.10 and i'm having a problem i don't know how to get back to Windows 7 i turn on the computer and it boots up GRUB i pick Windows 7 on Grub and it loads then the screen goes white and reboots and i have to pick Ubuntu 9.10 i thought it automatically goes to dual boot but know i don't know how to do it i can't press F8 it dosen't work please help me!:confused:

---

### Post by rogue_0111 on 2010-01-23
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by CommanderTux64 on 2010-01-23
need help with gparted

---

### Post by NCLI on 2010-01-23
What do you need help to do?

---

### Post by CommanderTux64 on 2010-01-23
Part 2 i don't know which partition i installed ubuntu 9.10 in and where windows 7 is do i have to format windows 7 to do this

Is NTFS windows 7

---

### Post by NCLI on 2010-01-23
You may have to. Sounds like you messed up your Win7 install somehow. Try opening a terminal in Ubuntu and running "sudo update-grub" first though, then reboot.

Did you shrink the Win7 partition while installing Ubuntu?

---

### Post by CommanderTux64 on 2010-01-23
> **NCLI said:**
> You may have to. Sounds like you messed up your Win7 install somehow. Try opening a terminal in Ubuntu and running "sudo update-grub" first though, then reboot.

Did you shrink the Win7 partition while installing Ubuntu?

I think it said resizing partition i messed up windows 7

I did what you said NCLI and updated grub and rebooted what happened i don't see a difference

---

### Post by NCLI on 2010-01-23
Well, if you didn't defragment your Win7 install before resizing the partition, and if it wasn't a fairly recent install, you may have deleted some important files during the resize. Please try running the command I posted first though, then come back if that doesn't work.

---

### Post by lisati on 2010-01-23
> **CommanderTux64 said:**
> 
Is NTFS windows 7

Maybe. The recovery partitions that came on my laptop (Vista Home Premium) and my main desktop (XP) were NTFS as well.

How are you getting on with the suggestions the others have made?

---

### Post by CommanderTux64 on 2010-01-23
It didn't work :confused:

---

### Post by NCLI on 2010-01-23
Could you please post your partition layout according to gParted or the Disk Manager?

EDIT: Just run "gksudo fdisk -l" in a terminal and post the output here.

---

### Post by kansasnoob on 2010-01-23
Please post the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

That should give us the info we need to try and get this sorted out.

Oh, and is it only Windows that won't boot?

You can boot into Ubuntu?

---

### Post by raymondh on 2010-01-23
From your other thread ... Did you do a WUBI-install or did you install Ubuntu in its' own partition?

---

### Post by kansasnoob on 2010-01-23
Look in your other thread:

[http://ubuntuforums.org/showthread.php?t=1388885](http://ubuntuforums.org/showthread.php?t=1388885)

We need the output of that Boot Info Script and possibly more info so we can troubleshoot this properly.

Calm down, take a breath and we'll see what's going on :)

---

### Post by cariboo on 2010-01-23
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by kansasnoob on 2010-01-23
> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged your two threads.

Thanks.

---

### Post by zipperback on 2010-01-23
> **CommanderTux64 said:**
> It didn't work :confused:

Oh well that just tells us SO MUCH useful information....


Please tell us the following information so that we can actually help you.

Please tell us the exact method that you used to install Ubuntu.

Which version of Ubuntu are you using? 64bit vs 32bit, etc.

Did you resize your Windows partition before installing Ubuntu? if so, HOW did you resize it? 

Please tell us what your partition table looks like.
To better help you, it would be good if we could know what exactly we are dealing with. If you don't have it installed already, please install gparted so we can get a screenshot of your partition layout.

To install gparted do the following.

```

Applications -> Accessories -> Terminal

sudo apt-get install gparted

```

It will ask you for your password, enter it and allow the application to be installed.

Once it is installed you can launch it with the following.

```

System -> Administration -> GParted

```

It will prompt you for your password.

Now take a screenshot.

```

Applications -> Accessories -> Take screenshot

```

A screenshot will help us understand the layout of your drive.

Once you have done the above stuff, we can work more towards getting your system running if possible.

Please have some patience and understand that while we are willing to help you, the end result will really depend on you educating your self on how to do things correctly.

- zipperback
:popcorn:

---

