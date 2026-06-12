---
title: "use windows to access ubuntu's hdd wireless"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by jdkelly022 on 2006-10-22
i already have a wireless network set up between the two different computers.  i want to know how to either use my windows computer to access the ubuntu's hdd or use the ubuntu hard drive to copy files over to the windows computer..any ideas?

---

### Post by punx45 on 2006-10-22
if both computers are connected to the network at the same time you have a few options.

easy: install openSSH server on the Ubuntu machine, and an SFTP client on the windows machine, use SFTP to log in to ubuntu machine and transfer files back and forth.

harder? this i have not done so i am not sure how difficult it will be:   using SAMBA you would be able to mount a networked drive from one machine onto another.   basically your windows machine would see a HDD on your ubuntu machine and you would use it similar to a normal drive.

there are probably other options too.

---

