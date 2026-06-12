---
title: "Dual boot Win 7x64 10.04lts"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by eric702 on 2010-07-23
I have win 7 on my primary Hard drive.  I've added a 2nd hard drive where I'd like to unbuntu without making any changed to windows 7.  I'm a noob to linux, but i used to use system commander or something like that back in the day for dual booting.  Does something like that exist now or is their a guide to do this.  Lastly, does 32 bit ubuntu see more than 3gb or ram or do you need x64 to accomplish this?
Thank you!

---

### Post by matrixblue on 2010-07-23
Boot from the Ubuntu Live CD and run the installer. Set Ubuntu to install to the second hard disk.

Your Windows installation will be unaffected but the Master Boot Record on that disk will be changed so that you can select which operating system you wish to boot to when you turn the computer on

---

### Post by oldfred on 2010-07-23
Be sure to use the advanced button or grub may install its bootloader to the windows drive. Lucid screen is identical to Karmic for knowing where the advanced button is.

Install karmic Screens shown with advanced button
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Mark Phelps on 2010-07-24
> **eric702 said:**
> I have win 7 on my primary Hard drive.  I've added a 2nd hard drive where I'd like to unbuntu without making any changed to windows 7. 
With a multi-drive system, my advice (which is what I do) is to disconnect all the drives except the one you'll be using to install Ubuntu.  This prevents the problem of accidentally installing GRUB to the other drive.

>  I'm a noob to linux, but i used to use system commander or something like that back in the day for dual booting.  Does something like that exist now or is their a guide to do this.  
GRUB (or more currently, GRUB2) accomplishes this by generating a menu that allows you to select among OSs.

> Lastly, does 32 bit ubuntu see more than 3gb or ram or do you need x64 to accomplish this?
Thank you!
32-bit Linux OSs suffer from the same limitations as other 32-bit OSs -- they won't see much more than 3GB of memory, no matter how much you have installed.

---

