---
title: "Printer issue"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by Geran on 2008-02-11
I am getting this error from the cups web admin page for my system...

Unable to connect to CIFS host, will retry in 60 seconds...

This is an HP Laser Jet 1020 printer that my linux system is trying to use over SMB.

Everything looks ok, it finds it on the network no problem, it even has the exact driver for the model number and description, it says everything is working, except for that error that I get.

thanks in advance,

G

---

### Post by briantipton on 2008-02-14
I ran into this trying to get my wifes Mac to print to a HP Laserjet 1200.  Turned out to be a permissions issue.  She wasn't connecting to the printer as a registered samba user.  I fixed the accounts to match and made sure the passwords matched and voila, we printed.

It could also be a DNS issue, but I don't know what your network looks like.

Since then, I have dropped the samba printing and gone straight to letting Mac OS and Windows print via CUPS.

Brian

---

