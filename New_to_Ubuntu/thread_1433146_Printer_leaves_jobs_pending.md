---
title: "Printer leaves jobs pending"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by Cera on 2010-03-18
I'm using ubuntu 10.04 Lucid Lynx.  The printer used to work just fine, and then it stopped printing.  The test page worked, and it would print.  Then it started printing about the first three pages of any document and leaving the job pending forever, and now it just leaves it pending.  I've tried messing around with it, but I can't figure out whats wrong.  Navigating the help pages hasn't gotten me far. 

This is the one thing I tried to troubleshoot, but after that I couldn't figure out what to do.

cera@cera-laptop:~$ /usr/lib/cups/backend/hp

direct hp "Unknown" "HP Printer (HPLIP)"

If anybody can help it would be fantastic, rebooting in windows everytime I want to print something is a pain in the ***....

---

### Post by xopher_mc on 2010-03-18
Hi

open firefox and put 

localhost:631

you should be able to control everything about you printer there. I reckon there a failed printing or something. Flush the queue and then it should all work fine.

---

### Post by erikthedrink on 2010-08-31
That brings me to the CUPS 1.4 page.  Did it used to do something more useful?

---

### Post by jcolyn on 2010-08-31
Try clicking the printer applet in the taskbar. Any pending jobs can be deleted from here...

---

### Post by cariboo on 2010-09-01
> **erikthedrink said:**
> That brings me to the CUPS 1.4 page.  Did it used to do something more useful?

Did you try clicking Administration->Manage Jobs?

---

### Post by Sef on 2010-09-01
What printer do you have?

---

### Post by sussexslanter on 2012-02-10
Did this get sorted somewhere else?  I have an Epson R300 and the same thing happens to me.  Just leaves it pending.  Is it an OpenOffice problem do you think?

---

### Post by sussexslanter on 2012-02-10
Aha - here's a tip for people with no knowledge.  Like me.

Try going to printer properties => policies. Tick the enable printer box! Works.

Quite why any update would have disabled my printer for me is beyond my knowledge.  And actually perhaps I never want to get that clever...

---

