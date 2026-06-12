---
title: "bcm4311 works, but not with NetworkManager"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by misha680 on 2007-02-10
Hi, I must say I do not consider myself an Ubuntu newbie, and have successfully installed and used Ubuntu on several computers (including one with a Broadcom card with an identical version number that worked fine) but I'm a little stumped. The computer is a $500 Compaq Presario C501NR that I bought for my mom, and I put Dapper Drake on it. I used the latest version of ndiswrapper (latest stable from sourceforge) and the computer came with a driver bcmwl6 which I assume is 6 and not 5 because of Vista, which did not work with ndiswrapper, but I just found a bcmwl5 on the Internet, installed that, wireless light is on, and I can connect just fine using iwconfig and dhclient. However, no go for NetworkManager, it detects all the wireless networks fine, but then doesn't connect and times out after 60 seconds. I tried NetworkManager CVS, which actually doesn't see my wireless networks anymore, and tried looking through the logs and saw that wpasupplicant is having trouble connecting and that it is using -Dndiswrapper (I've seen some sources recommand using -Dwext but I don't know how to change the driver NetworkManager tells wpasupplicant to use). Anyway, if anyone has seen this problem, I would appreciate any help. I've set up networkmanager successfully on all the other machines I've tried, including one with another broadcom card that i got working through ndiswrapper, so I'm a little thrown off by this.

Misha 

p.s. Also, since I installed Ubuntu, I had to add Vista manually to the menu.lst and reinstall grub, and now when I boot Vista it goes to the starup scren where there is a progress bar that keeps moving but it seems to sit there for way too long (like thirty minutes) and never progress beyond that point. Anyone seen anything like that? I am absolutely not familiar with Vista at all, and really wish this computer had come with XP (my mom wants both Windows and Ubuntu).

---

### Post by misha680 on 2007-02-10
Ok, for the Vista thing I am going to try the rootnoverify option. For network-manager i am going to try to prevu 0.6.4 from edgy. Since my other install was also NetworkManager CVS but quite a while back maybe I need a newer networkmanager but not as new as the current NetworkManager CVS (I'll prevu wpasupplicant too).

Misha

---

### Post by misha680 on 2007-02-10
Ok, doing prevu from edgy for network-manager and wpasupplicant (along with some dhcp stuff that was required) fixed this problem for me. The Vista thing is still a problem (although my mom said she could live without Vista so I am not going to focus a lot on it right now :) ) but I will post it in a separate thread.

Misha

---

