---
title: "Print from Ubuntu to Windows Printer Driver"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by cnferntreegully on 2006-09-19
Hi, how do I get Ubuntu to print to a Canon MP780 printer connected on Windows machine?

If I have to install any software on WINDOWS machine I prefer to use LPR program for simple TCP/IP printing if possible.

Any inputs is appreciated!

---

### Post by mwcinc on 2006-09-19
Is the printer shared in Windows?
If so, then you should be able to access it using the following menu options:
System -> Administration -> Printing -> Printer -> Add.

When you add the new printer, select "Network Printer".

Regards,

M.W.

---

### Post by cnferntreegully on 2006-09-19
Hi mwcinc, thanks for that.
For some reason it doesn't appear on Ubuntu's Network Printer.  Both machines are on 192.168.x.x IP address and the printer on Windows machine is shared.

What else could be the issue??

---

### Post by thommo on 2007-03-10
I assume you have changed the dropdown in the next screen to read windows (smb)?
from here the next screen has a host section that when I clicked on it it wanted me to supply some sort of logon for the windows box (I used guest)

---

