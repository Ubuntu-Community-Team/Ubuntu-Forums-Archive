---
title: "How to get a connect to a printer via samba share?"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by Mundofr on 2008-04-01
Hello there,

I'm trying to set up a computer in my school that it's only for printing.  I recently installed ubuntu 7.10 on it because the computer is somewhat old.

I have to connect and disconnect frequently to a password-protected samba share, and each student has a username and a password that stores how many pages you've printed.  The printer is shared via that samba share.  My problem is that I cannot find the printer thru samba.

The printer is a HP Laserjet 4250 and it is shared with a Windows 2000 Server PC.  I can connect to the printer directly because it is a Network printer, but my Network Administrator wants me to connect it thru the server so it records the number of pages print.

Am I missing any information?

Is there a way to do what I'm trying to do?

---

### Post by superprash2003 on 2008-04-01
check your /etc/samba/smb.conf file and make sure 
  printing = cups
   printcap name = cups

is not commented

---

### Post by Mundofr on 2008-04-01
I already did, still not working :/

Isn't the problem over the Windows box?

---

