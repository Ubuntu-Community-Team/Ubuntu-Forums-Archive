---
title: "Wired Network not working?!"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by ljoslin on 2007-09-21
I recently built a new desktop from scratch.  I installed Fiesty on it at first w/o a problem.  Everything was working perfectly, then I realized I wanted to install Windows XP on a partition, so I cleaned the HD and installed windows.  Then reinstalled Ubuntu.  However now I can't connect to the network in ubuntu, oddly it works fine in Windows.  What would of changed when I installed windows?  Even booting off of the Live CD I get no network connection.  It's a built in Ethernet card on a MSI mother board.  Any help would be greatly appreciated! Thanks in advance,

LJoslin

---

### Post by kevdog on 2007-09-21
Can you post 
lshw -C network

You may have just been bitten by the realtek rtl bug that windows puts the card in state that only windows can recover from.  If lshw -C netwok does reveal a rtl type card, then do a search for user name noob12, or PM him since he has written a small how-to to get around this problem.

---

### Post by ljoslin on 2007-09-21
It found 

product:  RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.


so I guess I'm searching for Noob12  Thanks!

ljoslin

---

### Post by noob12 on 2007-09-21
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

