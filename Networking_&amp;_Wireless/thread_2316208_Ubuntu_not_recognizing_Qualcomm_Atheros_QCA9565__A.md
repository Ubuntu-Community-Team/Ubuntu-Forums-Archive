---
title: "Ubuntu not recognizing Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter"
date: 2016-03-06
forum: Networking &amp; Wireless
---

### Post by TheAmazingJuicyBea on 2016-03-06
I have tried asking /r/LinuxMasterRace but have not gotten a response so far and all the methods I have tried so far are outdated and lead to 404'ed pages. I have a ASUS Dual-Band Wireless AC1300 Adapter with a driver CD which has worked on Windows 10 but not Linux. I have tried a How To Geek article suggesting I use Ndiswrapper but I get an error message stating "An error occurred while loading the archive." when you had to find sub folders in a .exe file. I downloaded the drivers from the ASUS website and tried running the autorun.inf file in the DR_USB_AC55_1008 folder with Ndiswrapper but get an error message while installing. The .inf folder simply says 

[autorun]

Open=setup.exe


icon=setup.ico 

Though I am not sure if that matters. Some tutorials use this link: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.4-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.4-1.tar.bz2) but it 404's and this tutorial [http://ubuntuforums.org/showthread.php?t=2172044](http://ubuntuforums.org/showthread.php?t=2172044) did not seem to work for me.


Any suggestions would be greatly appreciated.

---

### Post by Bucky Ball on 2016-03-06
Please see the wirelessinfo script link in my signature at the bottom of this post, run that script, post the output here between code tags (also how to linked in my signature).

Please provide links to anything you tried (like the first how to that advised installing ndiswrapper) otherwise we are flying blind. Ndiswrapper is obsolete in most circumstances and for most cards now and you may need to get rid of that before progressing any further.

* Not sure how far you followed the bread crumbs from the link you did post, but [this is what chili555 is talking about]("http://ubuntuforums.org/showthread.php?t=2103062&p=12451838&viewfull=1#post12451838").

As you have ndiswrapper installed, though, most things that would fix this probably won't until you get rid of it.

---

### Post by TheAmazingJuicyBea on 2016-03-08
> **Bucky Ball said:**
> * Not sure how far you followed the bread crumbs from the link you did post, but <a href="http://ubuntuforums.org/showthread.php?t=2103062&amp;p=12451838&amp;viewfull=1#post12451838" target="_blank">this is what chili555 is talking about</a>. The link used in the solution for wget no longer works which is the issue I am having as most mirrors appear to 404. I will run the script again when I can connect my Linux computer to the internet.

---

### Post by jeremy31 on 2016-03-08
This one should work
```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz
tar -zxvf backports-20151120
make defconfig-ath9k
make 
sudo make install
```

Reboot

---

### Post by Responsive on 2016-07-21
[I]make: *** No rule to make target 'defconfig-ath9k'. Stop.

any help?[/I]

---

### Post by jeremy31 on 2016-07-21
The backports are too old to build on a 4.4 kernel and your issue is a hard block which is something backports can't usually fix

---

