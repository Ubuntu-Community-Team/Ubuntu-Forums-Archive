---
title: "Ubuntu does not detect internet, but Vista does"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by igor1102828 on 2007-06-16
I have Vista and XP on one disk and Ubuntu 6.06 on the other one. Vista sees internet all the time without problems. Ubuntu does not. I've tried to boot the comp from the live CD, then the connection was restored. I switched off computer, removed CD and has booted Ubuntu from disk. Internet worked. Next morning when I started computer in Ubuntu, the internet connection was absent again. Re-booted into Vista, the connection is excellent.

I can boot in into Ubuntu only under "noapic" option (otherwise it hangs on early stage with the message:
"MP-BIOS bug: 8254 timer not connected to IO-APIC"; I added into /boot/grub/menu.lst "noapic").

The folder /etc/ does not contain subfolder sysconfig

ethernet etc0 is active, dhcp is used (NOT static), sudo ping (N router) does not see server.

I compared the options in "Networking"  in this desktop with those options in laptop, where XP and the same Ubuntu live on the same disk and where the inet connection does work. They are the same!](*,)

Please, help to solve this puzzle!

---

### Post by igor1102828 on 2007-06-16
Something really strange! Now, after using Vista, I have booted into Ubuntu and the internet connection has appeared again! It looks like someone else, not me, controls the situation!

---

### Post by ronmaroria on 2007-07-03
got a similar problem here. i would be browsing the Internet and then all of a sudden, there is no Internet. i still have dhcp enabled and set to automatic. my eth0 is enabled. when i restart and go to xp, i have Internet.

i am running feisty.

---

### Post by smo0th on 2007-07-03
just be sure you don't have duplicate DNS, check my previous post:

[http://ubuntuforums.org/showthread.php?p=2472174#post2472174](http://ubuntuforums.org/showthread.php?p=2472174#post2472174)

---

