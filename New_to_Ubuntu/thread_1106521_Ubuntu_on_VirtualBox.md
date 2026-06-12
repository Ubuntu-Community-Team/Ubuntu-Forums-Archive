---
title: "Ubuntu on VirtualBox"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by PoisonSerpent on 2009-03-25
Hello,

I am new to Linux, so please bare with me.

I have a 64bit machine that I have VirtualBox on. I am running WindowsXP SP3. I downloaded the 64bit version of Ubuntu from the website, and I loaded it into VirtualBox. I set the defaults for the RAM, and I put 8GB for the Virtual Hard Drive (fixed size). When I run, it gives me the language selection (I choose English), and then I push Install Ubuntu, and the system just "hangs". I can go back to Windows and it works fine. It does the exact same thing when I go to the "Just Run Ubuntu without changing my computer" option.

Can anyone help? VirtualBox works just fine with Slax.

--
*PoisonSerpent*

---

### Post by Old_Grey_Wolf on 2009-03-25
Have you checked to make sure your download and/or burn was good? Such as check the MD5.

---

### Post by PoisonSerpent on 2009-03-25
> **Old_Gray_Wolf said:**
> Have you checked to make sure your download and/or burn was good? Such as check the MD5.

Well, I don't have access to the computer right now (it's at school), but should I just redownload the .iso file and then try it?

---

### Post by Old_Grey_Wolf on 2009-03-25
You can redownload it if you want. I don't use Windows XP so I can't tell you how to check the MD5 on what you already downloaded. I find that I get better, less errors, from torrent downloads rather than downloading from a server.

---

### Post by DGortze380 on 2009-03-25
> **Old_Gray_Wolf said:**
> You can redownload it if you want. I don't use Windows XP so I can't tell you how to check the MD5 on what you already downloaded. I find that I get better, less errors, from torrent downloads rather than downloading from a server.

google hashcalc to check the md5

---

### Post by Old_Grey_Wolf on 2009-03-25
To download using a torrent go to [http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

Edit: There is also a Sub-forum on Virtualization with discussions on Virtualbox, VMware, Zen, etc., here [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308). You may be able to search for your current question and future ones there.

---

### Post by PoisonSerpent on 2009-03-25
> **Old_Gray_Wolf said:**
> To download using a torrent go to [http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

Edit: There is also a Sub-forum on Virtualization with discussions on Virtualbox, VMware, Zen, etc., here [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308). You may be able to search for your current question and future ones there.

It seems the documentation states how to install **VirtualBox** on _Ubuntu_. I want to install _Ubuntu_ on **VirtualBox**. Thanks for the link, though. Will try again tomorrow with the new .iso, since I don't have access to the computer right now.

---

### Post by PoisonSerpent on 2009-03-26
My friend gave me a LiveCD of Ubuntu 7.10 (Gutsy Gibbon) and it worked fine when I installed it. Something about 8.10 made VirtualBox not like me.. Oh well, I'm posting this on Ubuntu now, so I guess that means it works!


Thanks for all the help!

---

### Post by CowzRule on 2009-03-26
What version of Virtualbox do you have? In order to run a 64 bit guest os you must have version 2.0 or higher.
This is from the help file from Virtualbox
> Starting with Version 2.0, VirtualBox also supports 64-bit guest operating systems. Starting with Version 2.1, you can even run 64-bit guests on a 32-bit host operating system, so long as you have sufficient hardware.
In detail, 64-bit guests are supported under the following conditions:
You need a 64-bit processor with hardware virtualization support (see Section 1.2, “Software vs. hardware virtualization (VT-x and AMD-V)”).
You must enable hardware virtualization for the particular VM for which you want 64-bit support; software virtualization is not supported for 64-bit VMs.
Note
On most systems, the hardware virtualization features first need to be enabled in the BIOS before VirtualBox can use them.

---

### Post by PoisonSerpent on 2009-03-26
> **CowzRule said:**
> What version of Virtualbox do you have? In order to run a 64 bit guest os you must have version 2.0 or higher.
This is from the help file from Virtualbox

I have version 2.1.4, with 1GB of ram and a 8GB Virtual Hard Drive. I use Ubuntu 7.10.. it installed fine. But man, does the apt ever take ***_long_*** to check the mirror (around 20 minutes for me), but after that, it ran like a breeze. I decided to use Ubuntu for a radio station (I have a dedicated PC for it) for my school, and I think it will work out great.


Thanks for all the help, guys.

---

