---
title: "Unable to recognize my Ethernet port on Eee Ubuntu"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by lenelson on 2009-01-28
I am running Ubuntu for Eee on my Asus Eee. I was trying to use the little notebook to do some testing on a LAN without WiFi and I do not have an ethernet port according to Ubuntu. When I was using the Asus version of Linux, the 10Base-T port worked. Is there a way to find the ethernet port?
I should add: my system seems to miss-identify my RJ-45 port as a modem. When I click on "Network" program. It show WiFi and Point to Point (modem) settings. I sure will appreciate some help!

---

### Post by Iowan on 2009-01-28
Try **lshw -C network** (in a terminal) to see if it discovers the ethernet interface.

---

### Post by lenelson on 2009-02-08
The system sees the WiFi but that is all, a great utility, thanks.

---

