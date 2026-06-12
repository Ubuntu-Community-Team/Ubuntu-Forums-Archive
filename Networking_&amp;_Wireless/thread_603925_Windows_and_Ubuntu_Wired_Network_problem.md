---
title: "Windows and Ubuntu Wired Network problem"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by dinhviet on 2007-11-05
I'm using both Windows and Ubuntu on the same HDD with different partitions.

I had the problem with Ubuntu's no internet connection before and I solved it by unplug the power and the cable.
However, whenever I boot up with windows, restart computer and login to Ubuntu, there're no internet connection again.

Repeating the unplug process again and again is such an annoying thing.
Any idea?:confused:

---

### Post by oldgeezer1 on 2007-11-05
I had the same problem.  Another thread solved the problem for me but for the life of me, I can't find it to update it.  So, I'll pass along to you what I learned from the other poster.  FWIW, I'm running XP Home on the Windows side.

In Windows, do the following:

1.  Start - Settings - Control Panel
2.  Click on Systems - Hardware - Device Manager
3.  Double-click on your ethernet card
4.  Click the "Advanced" tab
5.  Select the Wake-on-Lan After Shutdown
6.  In the box to the right change "disable" to "enable"
7.  Click on "Ok" and exit normally.

What was happening was that when Windows shut down, it brought the ethernet modem down with it.  

I hope that fixes your problem.  Let us know if it did.

---

