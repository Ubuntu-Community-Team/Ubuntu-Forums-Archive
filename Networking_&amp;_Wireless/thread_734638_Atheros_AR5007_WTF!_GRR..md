---
title: "Atheros AR5007 WTF! GRR."
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by Buckwheat469 on 2008-03-24
Here's my problem. I have an Atheros AR5007 in Windows Vista. It's considered an Atheros AR5006EG in Ubuntu 7.10 for whatever weird reason. I've tried following every direction in ndiswrapper and madwifi, but when I start the driver (or when I think I'm starting the driver) it doesn't show a new network in the network manager.

I wouldn't mind installing whatever drivers I need, then rebooting and magically seeing a new Wireless network option in the network manager. I really shouldn't need to have a Comp Sci degree to run Ubuntu on this computer. Anyway, enough with my tiny rant, it's still better than Windows.

Can someone please show me the answer?

**Computer Info**:
HP dv6768se
Atheros AR5007 (shown as AR5006EG in Ubuntu)
Ubn2 (short for Ubuntu) 7.10
Kernel 2.6.22-14-generic

Thank you very much.

---

### Post by AlanB66 on 2008-03-25
Not completely done installing, but noticed the wireless device in the network icon after installing 8.04 beta:

[http://ubuntuforums.org/showthread.php?t=687833&page=4](http://ubuntuforums.org/showthread.php?t=687833&page=4)

---

### Post by kevdog on 2008-03-26
This thread lists some links -- Do a forum search this problem has been discussed several times within the last month and solutions have been found -- patched madwifi driver if I remember correctly.
[http://ubuntuforums.org/showpost.php?p=4259805&postcount=14](http://ubuntuforums.org/showpost.php?p=4259805&postcount=14)

---

### Post by which_chick on 2008-03-26
[http://ubuntuforums.org/showthread.php?t=732945](http://ubuntuforums.org/showthread.php?t=732945)

Shows the same problem, plus step-by-step to get it working.  The solution used was the snapshot-patched madwifi driver.

Good luck!

---

### Post by styyle14 on 2008-04-01
Ubuntu needs to fix the original detection of the wireless card, madwifi would probably work un-patched if it correctly identified the wireless card.  I have a toshiba a135 and it rellay bugs me that other linux distros have perfect compatibility for this wireless card on their live cd's, yet ubuntu doesnt.

---

