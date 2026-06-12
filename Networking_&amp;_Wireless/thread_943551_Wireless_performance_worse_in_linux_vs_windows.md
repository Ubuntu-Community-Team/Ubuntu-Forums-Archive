---
title: "Wireless performance worse in linux vs windows?"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by IanKoro on 2008-10-10
I have had to temporarily move my netgear router to another part of my house.

I have a Dell Inspiron 1420 dual booting Ubuntu 7.04 and Vista.

The wireless was working fine until I moved the router, but now when in Linux, I have trouble connecting at all, and when I can connect, it runs slowly and disconnects often. Everything still runs fine in windows. If I go to the other side of the house by the router, it works fine in Windows & Linux, and connecting to networks in other locations works fine, but I've found when the signal is weak, I have more luck with Windows.

Any ideas how I might fix this?

---

### Post by IanKoro on 2009-01-29
Well, I posted this ages ago, and the problem still persists, only now I've seen it in several locations. Places where Vista on the same machine has no trouble whatsoever, in Linux I can only rarely connect, and when I do, the behaviour is really sketchy. There will be 10 minutes where pinging anything says "Destination host unreachable", while it claims to be connected with a strong signal. Nothing like this ever happens in windows.


Anyone?

---

### Post by IanKoro on 2009-01-29
bump?

---

### Post by Ayuthia on 2009-01-29
The drivers for Linux and Windows are two different drivers.  Because of this, the performance of the two drivers are different.  Probably more times than not, the Linux driver is not going to work as well as Windows.  Most companies will mainly write drivers for Windows just because of the number of users.  Since they are proprietary, the Linux developers have to try and make a driver that works for Linux.  So as time goes along, the Linux drivers improve.

Just in case there is someone that might provide more helpful information, can you post your lspci -nn and lshw -C network information and if your card did not work out of the box, can you also let us know what you are using to make it work?

---

### Post by dmderoeck on 2009-01-29
The two are entirely different but and do not have any experience... that being said I'd always pick the performance of Linux over Windows;)

---

### Post by snuffy on 2009-07-02
I have the same problem with a toshiba satellite pro L40. the performance online is terrible on 9.04, sooo slow compared with xp. and my connection is at 70% at 3 feet from the router!

Would love to know how to fix this problem.

---

### Post by Dragonbite on 2009-07-02
> **Ayuthia said:**
> The drivers for Linux and Windows are two different drivers.  Because of this, the performance of the two drivers are different.  

What about if you use ndsiwrapper? Then it's the Windows driver being used, though I am sure it doesn't integrate as tightly as it will with Windows.

---

### Post by Ayuthia on 2009-07-02
> **Dragonbite said:**
> What about if you use ndsiwrapper? Then it's the Windows driver being used, though I am sure it doesn't integrate as tightly as it will with Windows.

The performance is not quite the same.  I have tried it out once before and in some cases ndiswrapper did not work as well.  Of course, I have also encountered cases where Linux worked better than Windows too.  

The main difference with NDISwrapper is that the code for NDISwrapper is written for Linux so how it deals with the Windows driver is different.  However, in my experience, the performance has always been pretty close.

---

### Post by Qchan on 2009-12-01
[b][color=darkred]
I found the solution. Appears to have a lot to do with the drivers. I had a similar issue on my Ubuntu laptop. I'd even have the antenna on the router touch the top lid of the laptop and still get about 60% which didn't make any sense at all!

Then I went here:
[http://sprayfly.com/2009/11/17/improve-wireless-performance-in-ubuntu-karmic-on-asus-eeepc-1005ha/](http://sprayfly.com/2009/11/17/improve-wireless-performance-in-ubuntu-karmic-on-asus-eeepc-1005ha/)

Follow those instructions and you should be all set. If that's too much of a hassle for you to do, then basically it tells you to install the backports wireless drivers. You can do that by enabling them in the software sources and then opening terminal and typing:

[/b][/color]
> 
sudo apt-get update && sudo apt-get install linux-backports-modules-wireless-karmic-generic

[b][color=darkred]

This only applies to Karmic Koala, but it should be available in other versions of Ubuntu if you just change the name of whats there.
[/b][/color]

---

### Post by Cuco3 on 2009-12-10
> **Qchan said:**
> [B][COLOR=darkred]
I found the solution. Appears to have a lot to do with the drivers. I had a similar issue on my Ubuntu laptop. I'd even have the antenna on the router touch the top lid of the laptop and still get about 60% which didn't make any sense at all!

Then I went here:
[http://sprayfly.com/2009/11/17/improve-wireless-performance-in-ubuntu-karmic-on-asus-eeepc-1005ha/](http://sprayfly.com/2009/11/17/improve-wireless-performance-in-ubuntu-karmic-on-asus-eeepc-1005ha/)

Follow those instructions and you should be all set. If that's too much of a hassle for you to do, then basically it tells you to install the backports wireless drivers. You can do that by enabling them in the software sources and then opening terminal and typing:

[/COLOR][/B]

[B][COLOR=darkred]

This only applies to Karmic Koala, but it should be available in other versions of Ubuntu if you just change the name of whats there.
[/COLOR][/B]I was really hoping this worked because I was experiencing the same symptoms as you (65% at best when laptop is right next to wireless access point). Unfortunately, it doesn't find the package for Jaunty.

---

