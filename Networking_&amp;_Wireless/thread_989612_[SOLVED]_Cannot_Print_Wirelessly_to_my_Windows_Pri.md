---
title: "[SOLVED] Cannot Print Wirelessly to my Windows Printer"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by gjr5017 on 2008-11-21
I cannot add my printer to Ubuntu for some reason. I had it working before, no problem but when I go to add printer there is no option for something like "windows printer attached w/ samba" or something like that that there was before....help please.

I'm running Hardy.

Edit: Should specify that I do have samba installed and I can share my storage partition over the network and access it on a windows XP computer just fine....didn't try our vista one, but the printer is connected to the XP one.

---

### Post by spcwingo on 2008-11-22
Have you added the host via System>Administration>Network>hosts?  I think that it also helps if the host is using a static ip address.

---

### Post by superprash2003 on 2008-11-22
do you have the samba client installed?

---

### Post by spcwingo on 2008-11-22
Yes I do...hmmm...try installing the smbfs package also.  Let me know if that works.

---

### Post by gjr5017 on 2008-11-25
Sorry for the long response but I installed the smbfs package and now I can connect to the printer and print from it. Thanks :)

---

### Post by spcwingo on 2008-11-26
I'm glad I could help you get it going.

---

