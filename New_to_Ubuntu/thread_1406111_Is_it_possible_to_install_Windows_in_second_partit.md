---
title: "Is it possible to install Windows in second partition?"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by marktebbutt on 2010-02-13
Hi y'all,
I have recently bought a new PC and have loaded Ubuntu 9.10 as the primary OS. I partitioned the disk and left a second partition as NTFS - only reason really being iTunes. However, when I now try to install Windows it doesn't let me. I'm guessing it's a Windows problem, but can anyone tell me if there is a way around this?
Thanks.

---

### Post by luckydeveloper on 2010-02-13
If you want to keep windows and ubuntu on the same machine, you have to first install windows and then Ubuntu. If you do the reverse, Windows will hide (kinda, i mean it wont display the boot menu) ubuntu and will take you directly to windows.

So, please install windows on a NTFS partition and then Ubuntu on the rest of your disk.

---

### Post by t0p on 2010-02-13
Welcome to Ubuntu!  Help documentation on dual-booting Ubuntu and Windows OS [here]("https://help.ubuntu.com/community/WindowsDualBoot") - you especially need to read [this bit]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu") for info on installing Windows after Ubuntu.

---

### Post by paydaydaddy on 2010-02-13
It is possible but much more difficult than installing ubuntu on a partition after installing windows. I don't have any links to articles on this but I'm sure somebody will jump in with more help soon. If you are able to save what you need in your current install you may be ahead to wipe the hard drive and start from scratch with a windows install followed by your ubuntu install on a second partition. Ubuntu plays well with others, windows does not.

---

### Post by oldfred on 2010-02-13
I have saved lots of links, most have windows first, but show the processes, APC has one with linux first but uses old grub. You can install windows after Ubuntu, you just have to reinstall grub to the MBR as windows will overwrite it and if your 9.10 is a new install with grub2 sudo update-grub should find your windows to let you boot it. Just be carefull as some instructions are for grub legacy.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
See info on windows resizing, but do not agree with grub2 complaints
[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)

APC various dual boot graphical install
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)
Installing Ubuntu 9.10 Step-by-step installation tutorial with screenshots
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
Jaunty Jackalope / Windows7 Ultimate MultiBoot 'C' (with checkbox graphic for vista/7) 
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

Is your NTFS partition a primary partition? Windows will not install to a logical.

---

### Post by Shpongle on 2010-02-13
if you just need itunes , why not try run it in a virtual machine with win or better yet try an alternative , most of the linux /open source players are fantastic and i find them much more flexible and efficient than itunes or any windows based media player .

---

### Post by Easy Limits on 2010-02-13
Ya, you could just install windows in a virtual machine.

---

### Post by presence1960 on 2010-02-13
> **luckydeveloper said:**
> If you want to keep windows and ubuntu on the same machine,**_ you have to first install windows and then Ubuntu_**. If you do the reverse, Windows will hide (kinda, i mean it wont display the boot menu) ubuntu and will take you directly to windows.

**_So, please install windows on a NTFS partition and then Ubuntu on the rest of your disk._**

RE: Bold, underlined text above in quote.

That is so far from the truth. You do not have to install windows before ubuntu. You can install windows after ubuntu provided that you are putting windows on a primary partition. I have found instructions to installing windows XP on a logical partition by editing boot.ini but have not tried it myself ...yet!

Once you install windows it overwrites GRUB on the MBR and puts windows boot loader on the MBR. That is why the GRUB menu is gone. But don't panic your linux partition(s) are still there. All you need to do is a simple 1 minute process to restore GRUB to MBR & you will be good to go. Do not remove Ubuntu or any other linux OS just to install windows. That is a lot of extra work. Don't take my word, here are some links showing you how to install windows after Linux and one from our community showing you how to recover ubuntu after installing windows.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

P.S. I have windows in sda2 and windows was installed last after Ubuntu 9.10, Mint 8 & Sabayon 4.1

---

### Post by presence1960 on 2010-02-13
> **t0p said:**
> Welcome to Ubuntu!  Help documentation on dual-booting Ubuntu and Windows OS [here]("https://help.ubuntu.com/community/WindowsDualBoot") - you especially need to read [this bit]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu") for info on installing Windows after Ubuntu.

That how to will work with restoring legacy GRUB after installing windows. For GRUB2 [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") is the how to using the Live CD to reinstall GRUB2 on MBR

**_You are absolutely correct_**, I just wanted to add the GRUB2 instructions for restoring GRUB to MBR in case someone needs that!

---

### Post by jidan on 2010-02-14
yes, that's possible, but I think you have a lot of things to do.
The suhu has already told you and me how to install windows after ubuntu. This is a great forum :)

---

### Post by marktebbutt on 2010-02-15
Thank you for all the responses! I will try the install tonight...

I will also give Songbird a try instead of iTunes - I tried it in the past but reorganising all my music seemed like too big a job so I switched back. Now I will have to reorganise anyway as I have a new PC so will check Songbird out.

I'll mark this thread as closed, and once again thanks.

---

### Post by Paddy Landau on 2010-02-15
> **DillByrne said:**
> if you just need itunes ... try an alternative
AFAIK, you can update an iPod *only* with iTunes. If you've bought an iPod, then you need either Windows or Mac.

If I'm wrong, please let me know -- my daughter has to boot into Windows every time she wants to update her iPod, which was a gift. It would be so nice to be able to stay in Ubuntu to update it. (A virtual machine is not a good answer for me, because I don't want to purchase yet another version of Windows!)

---

### Post by Robster2 on 2010-02-17
You can run iTunes in WINE or Crossover Linux.

I would try those options first.  Much easier than dual booting or running a virtual machine.

Crossover Linux is not free but it is cheap and very easy to install Windows software.

[http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)

---

### Post by Paddy Landau on 2010-02-17
> **Robster2 said:**
> You can run iTunes in WINE or Crossover Linux.
According to both Crossover and [PlayOnLinx]("http://www.playonlinux.com/") (free), only versions 4 and 7 will work.

I'll install it through PlayOnLinux (which automates the installation), and get my daughter to test it. Thanks for the idea.

---

