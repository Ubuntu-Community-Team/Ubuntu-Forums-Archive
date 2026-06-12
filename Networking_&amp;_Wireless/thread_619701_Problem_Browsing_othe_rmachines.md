---
title: "Problem Browsing othe rmachines"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by root1492 on 2007-11-21
I have recently moved to ubuntu 7.10 from Fedora 8,  In fedora 8, right out of the box I could browse other machines  (win2K machines).

For some reason, in ubuntu 7.10, I can see the machines, but when I click them to browse, I get cannot display messages.  Can someone help me figure this out?

---

### Post by mpierce on 2007-11-21
Have you installed the samba packages? You need samba and samba-common and create a smb.conf file to share and access your windows machines. 

Otherwise, use an inbuilt protocol in Konqueror to access your other machine, i.e., 
   smb://192.168.1.252/mpierce

Typing that in Konqueror will allow me to access my home directory on my wireless XP laptop. BTW, smb protocol is samba so you need the packages.

---

### Post by root1492 on 2007-11-22
Yes.  Samaba packages are installed.

---

