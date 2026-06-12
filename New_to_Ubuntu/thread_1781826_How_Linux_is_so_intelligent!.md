---
title: "How Linux is so intelligent!"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by g_ramesh on 2011-06-14
Hi,

I am a newbie to Linux.  I have a pc with win xp / ubuntu on seperate partitions. After installing xp I had to install motherboard drivers to get all things like sound,video going. Apart from this I had to install LAN card driver , Printer driver seperately.

However after installing Linux (Ubuntu) straight away I started using the pc without the need for installing motherboard driver, LAN card or Printer driver. 

Ubuntu (for that matter any Linux OS might have done the same thing) automatically detected LAN card and printer and allowed me to use them straight away. How come this is possible only in Linux!   :cool:.

---

### Post by NightwishFan on 2011-06-14
> **g_ramesh said:**
> How come this is possible only in Linux!   :cool:.
Magic.

Well really being open source allows us to include drivers for the vast majority of hardware right in the kernel. :)

---

### Post by 3rdalbum on 2011-06-14
> **g_ramesh said:**
> However after installing Linux (Ubuntu) straight away I started using the pc without the need for installing motherboard driver, LAN card or Printer driver. 

Ubuntu (for that matter any Linux OS might have done the same thing) automatically detected LAN card and printer and allowed me to use them straight away. How come this is possible only in Linux!   :cool:.

Well, when you make the drivers as well as the kernel, it pretty much makes sense to distribute the drivers inside the kernel.

I've also heard that Linux kernel drivers share a lot of code with eachother - if a few different drivers all do similar things in one particular section, it will be factored out so they all call the same piece of code inside the kernel rather than all having a separate copy. In this way, Linux kernel drivers are smaller than their Windows counterparts.

---

### Post by slooksterpsv on 2011-06-14
Another thing that I see a lot of is 90% of my stuff is picked up by the kernel, new computers, old computers (I say 90% cause there may be an occasional device here or there, no worries though). And yet they can keep the kernel under 100MB and the whole OS packaged on a CD under 700MB. Yet Vista was up in the GB for the DVD, same with 7 and a lot of it is drivers.

If you've ever nLited an installation of your Windows to trim the fat yeah most of what you take out is drivers. In the Linux community people love open source, they make code and share it and get others to hop on board and change it, fix it, make it better.

Welcome to Linux, enjoy your PC, don't run it down with unnecessary scans for viruses, spyware, etc.

---

### Post by grahammechanical on 2011-06-14
Hi g_ramesh

Thank you for the positive comments. I was reminded of all posts that I have seen by Windows users complaining that they cannot get this or that working in Ubuntu but it works fine in Windows. Some people can be insulting as well. They forget that they buy a computer with the OS already installed and the maker has made sure that everything works before they sell the product.

With Linux the developers have the problem of producing an OS that has to work with as many types of computer hardware as possible and the OS is installed by the user who does not know how to fix things.

This is not only magic but genius.

Regards.

---

### Post by srs5694 on 2011-06-15
Another issue is that Windows XP is quite old. If your computer is newer than XP, then it probably *can't* have all the required drivers because some of the hardware is newer than the OS. Unless you're using an equally-old version of Ubuntu or a very new computer, the Linux kernel included with Ubuntu is probably newer than most or all of your hardware.

As others have said, if Windows came on the PC, the manufacturers could add the necessary drivers even if the hardware is newer than the OS; but when you re-install from scratch, you'll need to do this yourself.

---

