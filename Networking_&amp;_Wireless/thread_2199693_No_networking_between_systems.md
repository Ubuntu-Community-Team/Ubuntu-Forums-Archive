---
title: "No networking between systems"
date: 2014-01-15
forum: Networking &amp; Wireless
---

### Post by Glenn_Jarvis on 2014-01-15
I have a desktop and a laptop (both wireless) that are running 13.10, however I would like them to be able to access each others files (including hidden directories). The reason being is I want to transfer some data from the desktop over to the laptop. However, neither machine can see each other. I know Samba is installed and I have followed a few tutorials but they seem to be dated several years ago. Any help would be greatly appreciated. :)

Laptop reports Samba not installed. When asked to install service I receive error message "Package 'samba' is virtual" ??


Glenn

---

### Post by newbie-user on 2014-01-15
Try pinging the ip address of one computer from the other to verify that they're on the same network and actually can talk to each other. If they can, then I would suggest using scp instead of samba:

scp *[file you want to transfer]* *[user]*@*[other computer]*:/path/to/where/you/want/to/put/stuff

---

### Post by ian-weisser on 2014-01-15
newbie-user is right.
Samba is a great way to conveniently share files between multiple systems without much setup on each client...but the price is a lot of setup on the server.
If you're simply exchanging data between two systems, lighter options can be easier to configure, faster to use, and simpler to clean up.
If you're doing a one-time, one-way transfer then there are even easier methods than scp.

---

### Post by Bucky Ball on 2014-01-15
I use Filezilla and ftp for all that. No need for Samba unless you're networking with Win boxes. There's lots of ways (and more secure) of transferring data other than samba.

---

