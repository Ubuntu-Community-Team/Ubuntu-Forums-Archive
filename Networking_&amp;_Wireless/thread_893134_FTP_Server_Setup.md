---
title: "FTP Server Setup"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by gjr5017 on 2008-08-17
How would I go about setting up a small FTP Server on my ubuntu desktop that would allow me to share files with some people...my desktop is used everyday as a normal computer (basic word processing, internet usage, music playing/download, etc) so I still need it to be able to run efficiently. I'm not sure how I would go about setting it up just to be able to have my files be accessible no matter where I am.

---

### Post by mellowd on 2008-08-17
There are a number of ways to do this.

do you want to set it up so that an ftp daemon is always running in the background or do you want it so that you start it only if someone actually needs a file?

---

### Post by gjr5017 on 2008-08-18
If it's not too heavy on resources (I'm running a Laptop with an AMD Turion64x2 at 1.9 GHz with 2GB of RAM) I wouldn't mind running it 24/7 but if its a little heavy I could go the other route with it.

---

### Post by mellowd on 2008-08-18
> **gjr5017 said:**
> If it's not too heavy on resources (I'm running a Laptop with an AMD Turion64x2 at 1.9 GHz with 2GB of RAM) I wouldn't mind running it 24/7 but if its a little heavy I could go the other route with it.


It's not resourceful at all, in fact the process will sleep most of the time until it's required to actually do something.

A couple to mention is Pure-FTPd and vsftpd. Have a look at those

---

### Post by gjr5017 on 2008-08-18
> **mellowd said:**
> It's not resourceful at all, in fact the process will sleep most of the time until it's required to actually do something.

A couple to mention is Pure-FTPd and vsftpd. Have a look at those

I have Pure-FTPd installed but I can't find a way to actually like run it. I went through the read-me file which helped me install it and it says to run the one file which it does run but theres nothing that will allow me to change settings and pick folders to share on the FTP server.

---

### Post by gjr5017 on 2008-08-18
Any ideas?

---

### Post by gjr5017 on 2008-08-19
Help please.

---

### Post by jonwestin on 2008-09-22
Still having problems? Have you installed the GUI for pureftp? It works for me, only with actual users tho, cant get the virtual users to work.

---

