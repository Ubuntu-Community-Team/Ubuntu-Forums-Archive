---
title: "Do I need a super swap?"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by tonye25 on 2009-11-27
I have a P3 256MB ram 40GB hdd 

I was only able to get xubuntu livecd to boot to desktop with a 3-5GB swap.  Howerver, after I installed it, it never loaded past 1/4th of the bar during boot, then it froze.  Should I follow this thread: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)   to get it to boot like I need?  or should I make a bigger swap or something simular to insure a complete boot process?

---

### Post by Windows Nerd on 2009-11-27
The general rule with swap is 2x the size of your RAM, though I don't see how that much swap is needed to boot. I believe with 256 mb of RAM the minimal install of Ubuntu should work fine. A normal install can do fine with 512 mb of RAM. I see you are using Xubuntu (9.10?), there may be some bugs still left in the 9.10 version still, and many other people have problems with Xubuntu too.

Scott

---

### Post by tonye25 on 2009-11-27
> **Windows Nerd said:**
> The general rule with swap is 2x the size of your RAM, though I don't see how that much swap is needed to boot. I believe with 256 mb of RAM the minimal install of Ubuntu should work fine. A normal install can do fine with 512 mb of RAM. Maybe you might want to check out the minimal install. You can find it [here]("https://help.ubuntu.com/community/Installation/MinimalCD"). Remember to select the right install for you hardware.

Scott


so would i need this info?: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) 
would that help?

---

### Post by wilee-nilee on 2009-11-27
You should be installing with the alternative CD or even better the minimal install.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

With the minimal it just installs the basic system without the desktop applications so on restart you are at a command line just run sudo apt-get install xubuntu-desktop
The mini mal also install the ubuntu basic with all the updates.

Also P3 can have various chip speeds what is the max of yours.

---

