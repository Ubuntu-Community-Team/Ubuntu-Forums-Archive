---
title: "Intel 82566DC-2 Gigabit Network Connection problems."
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by hexbuntu on 2007-09-14
I just bought a HP Pavilion a6152n and installed ubuntu 7.04 on it. everything went fine with the installation except for the fact that i cant get my Intel 82566DC-2 Gigabit Network Connection to work. i have been looking on the forums  but cant seem to find anything to help me get this problem resolved(or if the  network card is compatible.)i am thinking about installing another network card to see if it works specifically with ubuntu.this is my first time using ubuntu or linux and any help would be greatly appreciated.

---

### Post by noob12 on 2007-09-14
Can you post the **lspci -nn** output (at least the line describing that card).  The device id may not be mapped by the version of e1000 that is in the distribution.  You may have to download and build a more recent e1000 driver from Intel.  Let's check first though.

---

### Post by noob12 on 2007-09-16
Check this thread:  [http://ubuntuforums.org/showthread.php?t=551720](http://ubuntuforums.org/showthread.php?t=551720)  and see if it applies to you.

---

