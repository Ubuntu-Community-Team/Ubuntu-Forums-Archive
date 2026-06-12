---
title: "HELP with file sharing between ubuntu 8.04 and Windows computers"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by stefboombastic on 2008-05-17
Hello everybody:cool:
 I entered Linux world with the new distro Ubuntu 8.04.
On my computer previously I had a WinXP pro sharing internet, files and printer with other PCs in my little home network..all worked perfectly.
I installed Ubuntu on my PC and I wished I could do the same. Following some posts online I managed to share my internet connection (ADSL).
But there is no way to share my files and folders in any direction, I mean it does not work both from Ubuntu to Windows machines (WinXP  pro, Vista ultimate) and from Windows PCs to Ubuntu.
I installed Samba and tried to configure it both with command line and with fronted tools.
In Nautilus I can see the Windows computers, but when I click on one I get no item at all! I am not prompted for any password!:confused:   From windows computers I am never prompted for passwords too and I always get something like I have no permissions.. ping works fine! 
On my PC I have 2 ethernet cards one connected to internet, the other with static IP 198.168.0.1 used for LAN used as gateway by other PCs.
I knew that Linux is much better than Windows on networks, but I managed to configure all my home network in 2 minutes on MS systems.. and now I've been getting crazy for days with Ubuntu without managing to do anything :frown:
PLEASE may somebody write down exactly how to do all? I can post  every conf file if needed! [-o<
THANK YOU VERY MUCH IN ADVANCE!
Stefano B.

---

### Post by joramdam on 2008-05-17
check this [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto+sticky](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto+sticky)

---

### Post by stefboombastic on 2008-05-17
THANK YOU INFINITELY MUCH!!! THAT DID IT!!!=D>

With that how-to, sharing from Ubuntu to Windows worked perfectly! 

Anyway browsing Windows shares was bugged in Nautilus with Ubuntu 8.04 as shown here:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

I followed the instructions in this thread and though I almost went crazy coz of dependances at the very end it fixed the problem :)

Again thank U! Hope next Ubuntu release can make things simpler :)

---

