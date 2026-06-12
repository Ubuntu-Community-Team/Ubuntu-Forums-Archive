---
title: "Canon MP540 Printer problems"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by bvpainter on 2010-04-02
I am having problems getting my Canon MP540 to work with 9.10.

I downloaded the drivers from Canon but when I try to install I get a message "cnijfilter-vcommon depends onlibcupsys2 (>2-1.2.1) however package libcupsys2 is not installed. I've searched synaptic for this file but cannot find it.

Any help please.

---

### Post by jaycee23 on 2010-04-02
Libcupsys2 has been superceded by libcup2 which is causing your problems.
Try the following thread - hope it helps
[http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248)

---

### Post by arnoversfeld on 2012-06-02
I own a Canon Pixma MP540 printer.
 The printer works beautifully in a Windows environment off my PC.
 In Ubuntu 12.04, which I use, Simple Scan works perfectly every time BUT printing is a problem.
 Any document will start printing but when it gets to the end of the document the page is not ejected. 

 The printer says it's busy printing and I get the impression it's waiting for something that just doesn't arrive.
 Ubuntu says it's finished printing but the printer doesn't agree.
 I have to pull the last page out of the printer by hand and pull the power plug to reset the printer.
 The printer setting in Ubuntu is A4 page size as is the Canon's setting.
What is printed is correct and good.


From my experience with other OS's of the past the printer is not getting an EOT (end of text) and / or an Eject page command.



 Is there a log report that will be  help in solving the problem ? How do I trace the problem (and solve it).

---

### Post by inashdeen on 2012-06-02
may i suggest upgrading to a newer version of ubuntu? chance are newer cups may fix the problem.

---

### Post by oldos2er on 2012-06-02
Old thread closed. Rather than post in an old thread, please start a new one.

---

