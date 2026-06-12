---
title: "Ntldr missing on install"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by BEESAGOLDFLASH on 2010-11-16
HI, I AM TRYING TO USE UBUNTU FOR THE FIRST TIME ON A TOSHIBA LAPTOP I BOUGHT BUT AM EXPERIENCING A STATEMENT OF NTLDR MISSING PRESS CTL ALT DEL TO START. WHAT DO I DO TO GET AROUND THIS. I AM A FIRST TIME USER FROM DOWN UNDER. CHEERS, DAVID...:confused:

---

### Post by Rubi1200 on 2010-11-16
Hi and welcome to the forums :)

Start by taking a look here:
[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

Hope this helps.

---

### Post by VinnyJ1701 on 2010-11-16
> **BEESAGOLDFLASH said:**
> HI, I AM TRYING TO USE UBUNTU FOR THE FIRST TIME ON A TOSHIBA LAPTOP I BOUGHT BUT AM EXPERIENCING A STATEMENT OF NTLDR MISSING PRESS CTL ALT DEL TO START. WHAT DO I DO TO GET AROUND THIS. I AM A FIRST TIME USER FROM DOWN UNDER. CHEERS, DAVID...:confused:

Hi David

Strangely, your problem sounds like a windows one, not a Ubuntu one.  Which ubuntu are you trying to use?

Did you try your ubuntu install with a live CD?  When you re-boot with a live CD in the drive, you can try ubuntu before the actual install.

Peace,

V.

---

### Post by Quackers on 2010-11-16
If your Ubuntu boots ok, or if not from the Live cd desktop
please go to the site below and download the boot script to your DESKTOP then open a terminal and run the command given on the first page of that site. This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by SOBravo on 2011-02-15
I am having a similar problem. I am new to Linux because I just got fed up with Microsoft. I am running Ubuntu from a LiveUSB. I tried to install Ubuntu 10.10 from the LiveUSB over and instead of Windows XP. Once completed, I restarted the computer (without the USB so it wouldn't boot to it) and I get the error "NTLDR Missing press ctl+alt+del to restart." I don't want windows any more nor will I ever go back to it willingly. What could I do to get past this?

---

### Post by b0b138 on 2011-02-15
The easiest thing would be to just reinstall again.  Because you're new with linux, it would be quicker, and getting familiar with the install process can't hurt.

For some reason it didn't install grub, which is the boot loader. The windows boot loader is still there for some reason, looking for windows (which it can't find)

If you want to try to fix it, go here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and towards the bottom is a section called reinstalling from grub2. Follow the "SIMPLEST - Copy GRUB 2 Files from the LiveCD" part.

---

### Post by SOBravo on 2011-03-05
Thank you b0b138! I got it working (for the most part) & I an content. The only issue now is that I have to select the boot drive. If I let my computer start normally, it can't find the boot drive. If I hit "Alt+f2" after the memory test I can choose to load from the hard drive (or the USB, CD ROM, etc.) It works for now, but I'd like to fix that too. I guess I'd need to create a start-up disk to fill in what is missing??

Thank you for your help!

---

