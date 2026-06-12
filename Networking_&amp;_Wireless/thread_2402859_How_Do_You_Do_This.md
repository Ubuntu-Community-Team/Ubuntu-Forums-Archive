---
title: "How Do You Do This?"
date: 2018-10-05
forum: Networking &amp; Wireless
---

### Post by captspicy on 2018-10-05
i have been a windows user for all my life and i'm pretty well versed and know my way around a computer but recently decided that i wanted to upgrade my old laptop and use it for school and during the upgrade i got a new SSD instead of hard drive. I decided since its running a 3rd gen i3 i may want to look for something a little less intensive then windows and I've always wanted to learn how Linux works. After some time i decided on Ubuntu Mate as it is very simple on my processor and offers a good community with a lot of support. However after using it for awhile i have found that anything more then a simple install of chrome is a hassle and seems much too difficult even for someone who has taken a couple classes working in various code languages. My biggest problem is that since the laptop is old the WiFi card is not in the best shape. Not a problem i went out and found a decent USB WiFi adapter that i knew works with Linux (Edimax N150) but to my disappointment no matter how hard i tried i couldn't seem to get the driver downloaded. I used the included disk, found updated drivers online, searched for hours trying to figure out how to get the driver downloaded and working to no avail. I know this is user error on my account but i also know that when i plug this into a windows pc it takes 1 or 2 clicks to get it working correctly. For now i will be going back to windows 10, I would still love to learn how to use Ubuntu and Linux if anyone knows any good Youtube channels or classes that i can learn from but for the time being its just far to steep of a learning curve and i want my simple lovely windows back.

---

### Post by yuioni on 2018-10-05
[https://www.youtube.com/watch?v=wBp0Rb-ZJak&t=10466s](https://www.youtube.com/watch?v=wBp0Rb-ZJak&t=10466s) 


I've been watching this to learn linux. it's a 7 hour video. but as for your problem i have no real answers as i'm also new.

---

### Post by NM5TF on 2018-10-05
@catspicy

we need more information to be able to even start to help you....

you say Ubuntu Mate is installed....which version ???

you say you downloaded the wifi drivers....which version ???

FYI....I use the very same dongle & have had no problems with it running Ubuntu, Fedora, Mint, Debian, openSUSE, or Arch Linux....

most OS will auto load the correct driver

post the output of

```
inxi -F
```

this will give needed information to get started

FYI...the correct driver for your dongle is found here  [http://https://www.edimax.com/edimax/download/download/data/edimax/global/download/for_home/wireless_adapters/wireless_adapters_n150/ew-7811un]("http://https://www.edimax.com/edimax/download/download/data/edimax/global/download/for_home/wireless_adapters/wireless_adapters_n150/ew-7811un")

tommy

---

### Post by oldos2er on 2018-10-05
Moved to *Networking and Wireless.*

Please see [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by oldrocker99 on 2018-10-05
Ubuntu MATE has a software center built-in. It will install Chrome with a click. If you haven't tried it yet, give it a shot.

Personally, having used a few distros in 10 years, Ubuntu MATE is, hands down, the best distro available, in any flavor. MATE is available for every flavor of Linux, but the main development work is accomplished by Martin Winpress, the man behind Ubuntu MATE, and that version gets the very latest version of my favorite desktop.

I HATE big icons, and UM has the desktop I fell in love with 10 years ago, only much improved.

Also, network cards which work on Linux already have the drivers in the kernel.

---

### Post by praseodym on 2018-10-06
Hi,

lets check the hardware in use with these commands (open a terminal with CTRL+ALT+T):
```

lspci -nnk
lsusb
```

---

