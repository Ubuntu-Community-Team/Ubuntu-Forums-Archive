---
title: "SiS video framebuffer problem"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by celticbhoy on 2010-02-13
I set my in-laws laptop up with Ubuntu 9.10 about a month ago as they were growing weary of XP. Everything has gone fine until the other night when my father in law was messing about in software store. He added a few packages, and deleted one by accident. He cant remeber what he deleted, or even which category it was from, but now the laptop crashes when try to start X.

Now when the laptop boots it shows xsplash then goes to a dialog screen which says :-

(EE) open /dev/fb0:no such file or directory

When I click <OK> I get a small menu with 

Run ubuntu in low-graphics mode
Reconfigure graphics
Troubleshoot
Exit to console

Reconfigure does no good, but I can get logged in to text install.

The laptop is an Acer Aspire 3630 and uses SiS graphics.

I have tried googling to find an answer, but I am at a loss, is there any way to fix this? how would I go about re-installing the full xserver? can I re-install 9.10, but keep the user accounts?

---

### Post by celticbhoy on 2010-02-13
Dont know is this helps any, but I removed & re-installed the xserver. still get the same error, but on tty7 I get a black screen with a terminal in the top left and the standard X cursor.

---

### Post by celticbhoy on 2010-02-13
Reading on google with other people with the same kinda problem, it might be the SiS driver.

how do I downgrade to an older version?

How do I find out the version installed?

---

