---
title: "Sharing a printer on ubuntu with windows PCs"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by clsyorkshire on 2007-01-26
Hi all, I'm a relative newbie on linux so please excuse the ignorance.

I'm running three PCs on a network, one PC running Dapper Drake, the other two running XP.

I have an Epson Stylus C62 connected to the Ubuntu PC using a USB cable. Basically what I want to do is to share the printer so that the other two XP PCs can print using it. This is where I get stuck.

How do I share the printer? I've tried clicking the properties on the Printer but I can't find any way of sharing it.

The network is running fine otherwise. I can share folders between all three PCs and that works fine. It's just the printer that's the problem.

The printer will print fine on the Ubuntu PC.


Thanks for any help. :)

---

### Post by renzokuken on 2007-01-26
i dont know the exact details but it can definately be done using CUPS and SAMBA. SAMBA allows the windows boxes to talk to the ubuntu box, and CUPS (common unix printing system) manages printers.

there are several excellent guides in this forum and others.

---

### Post by sabitha on 2007-01-26
i can print from my windows to the connect printer with ubuntu. all i have to just add network printer on windows with > [http://ip_printer:631/printers/name_printer](http://ip_printer:631/printers/name_printer) that&#347; it.

---

### Post by clsyorkshire on 2007-01-26
Fixed it now, thanks! :D

---

### Post by glurgle on 2007-01-27
This is the reply I was looking for :) No need to mess around with samba printer sharing at all :D

---

