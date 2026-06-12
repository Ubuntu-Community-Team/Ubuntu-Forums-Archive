---
title: "printer sharing to a windows server 2008 machine"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by tone33 on 2008-10-06
I have Ubuntu 8.04 running on my desktop machine.  And Windows Server 2008 running on my laptop (for my full time .net development job).  I want to share the printer from my ubuntu machine to the server 2k8 laptop.  I have done this successfully in the past with a Vista machine by following this advice:

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

But this doesn't work for Server 2k8.  I can browse to the cups page and print a test page from there, but when I add a printer and give it the url - which is [http://192.168.1.101/printers/HP_LaserJet_2100_Series](http://192.168.1.101/printers/HP_LaserJet_2100_Series) - windows tells me the standard can't find it message:

"Windows cannot connect to the printer.  Make sure that you have typed the name correctly, and that the printer is connected to the network"  

Any ideas?

---

### Post by superprash2003 on 2008-10-06
are you doing this via samba?? have you enabled printer sharing in the smb.conf file?

---

### Post by tone33 on 2008-10-10
ummm... not sure.  how would i find out?

---

### Post by tone33 on 2008-10-28
So.... any other ideas on this?

---

