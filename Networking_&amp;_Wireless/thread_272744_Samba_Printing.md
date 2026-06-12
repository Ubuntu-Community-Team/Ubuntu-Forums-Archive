---
title: "Samba Printing"
date: 2006-10-06
forum: Networking &amp; Wireless
---

### Post by sirhobbit on 2006-10-06
I have just installed Ubuntu Desktop on an old compuer to use as a mini-server. First job was to hand over print server duties from Windows to Ubuntu. 

After connecting the printer and printing a successful test page from Ubuntu I added the printer to Samba with the following conf lines:

load printers = yes
printing = cups
printcap name = cups
guest ok = yes
public = yes

I am able to print from my desktop but when the printer is added to the laptop the printer status shows 'Access denied, unable to connect'. I have made sure that the appropriate users were added to samba. The only things that are different etween the laptop and the desktop are that the desktop uses XP pro and the laptop uses XP home. The laptop uses windows firewall (tried disabling but to no avail) and norton anti-virus while the desktop uses zone alarm and avg free.

Any ideas cause I'm stuffed!

---

### Post by sirhobbit on 2006-10-06
Ok, I was just able to print something by turning Norton off. But printing from both windows machines is very slow. It takes about a minute to transfer the data to the server - this for a one line printer test page. Once ubuntu starts printing it goes at normal speed. Any ideas?

---

### Post by sirhobbit on 2006-10-06
Well both computers are now printing but when I open the printer dialog in widows it still says 'Access denied, unable to connect'.

---

### Post by David Corrales on 2006-10-12
I just added a username using **smbpasswd** and now I can use the printer from other Linux boxes.
Syntax: **sudo passwd -a username**
You'll get asked for a password.

---

