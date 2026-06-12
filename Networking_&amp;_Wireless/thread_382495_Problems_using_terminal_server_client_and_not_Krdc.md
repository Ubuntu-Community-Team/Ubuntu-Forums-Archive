---
title: "Problems using terminal server client and not Krdc?"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by cje on 2007-03-12
I'm experiencing a problem using the terminal server client; when I do start the TSC connection the screen goes black and the computer logs off.
(I'm testing on a Xubuntu system, PII, 500MbRam)

I've installed Krdc too, which perfectly connects to my Windows terminal server. 
Anyone who knows why Krdc works and not tsc?

I need to auto start an application when connecting to my ts. So, the Krdc is not preferable.

Thanks for any comments

---

### Post by cje on 2007-03-12
One more thing; 
the same thing happens when I type rdesktop [host name] in the terminal window

---

### Post by cje on 2007-03-13
I believe I found the problem by my self. Xubuntu is based on KDE. Rdesktop is made for Gnome. 
So, Xubuntu and the TSC does not work together .....

---

