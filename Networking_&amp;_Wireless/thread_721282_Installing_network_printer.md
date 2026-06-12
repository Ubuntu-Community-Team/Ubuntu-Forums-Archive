---
title: "Installing network printer"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by trm96 on 2008-03-11
I have a printer connected to my Mac (Canon i900D) and want to be able to use it to print on my notebook (Gutsy) and my desktop (Gutsy) both are wired. I have it up and working on another desktop (Vista) (wireless). Alls I had to do on the Windows machine is download bonjour and install it.

When I go into add printer on both my Gutsy machines it sees the printer but when I click verify it says "Inaccessible This print share is not accessible."

How do I connect to a printer via bonjour in Ubuntu?

Thank you for the help in advance...

---

### Post by handydan918 on 2008-03-11
You don't need bonjour. Mac uses CUPS (Common Unix Printing System) just like linux. I would start by checking to see that the make is set up to share the printer.
You may also need to install the drivers for the printer on the Ubu boxen....not sure.

---

### Post by trm96 on 2008-03-11
In Loepard I go into sharing in the system proprties and the only thing i see under prnter sharing is the printer and a check next to it.

---

### Post by trm96 on 2008-03-11
Ok well I have found the answer here: [http://mcdevzone.com/2007/10/28/printer-fix-for-leopard/](http://mcdevzone.com/2007/10/28/printer-fix-for-leopard/)

---

