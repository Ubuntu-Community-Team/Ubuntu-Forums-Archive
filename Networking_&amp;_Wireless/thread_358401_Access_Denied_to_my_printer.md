---
title: "Access Denied to my printer"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by Das Oracle on 2007-02-10
I am trying to share my printer with other computers that run windows. I can print fine from my computer and the other computers can view my printer but when I connect to it from windows i get an "Access denied, unable to connect" message after it installs the printer


* tried printer already and it sort of works * it print some things like hyperlinks in pdfs but just the windows logo in the printer test page. would this be related to having access denied?

---

### Post by FrankT-Qc on 2008-07-14
Hi.

Let's assume you made everything right to share your printer, you might want to double check a few things on the Windows side. I just had the same problem(s?) and here's what got me out of trouble:

First, make sure that the driver you use is the same on both side. Example : I have a Brother 2040 but Ubuntu runs it under the 2060 driver whitch works fine. Windows has the 2040 driver and will try to use it. If you're experiencing the same pattern, swith to the same driver as Ubuntu on your Windows boxes.

Another thing. Spooling from a Windows box seams problematic so i switched to "Print directly to the printer". Now, I still see "Acess denied" every now and then in some background grayed out message but printing works perfectly fine.

---

