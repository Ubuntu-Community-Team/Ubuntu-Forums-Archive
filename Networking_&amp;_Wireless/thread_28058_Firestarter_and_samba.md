---
title: "Firestarter and samba"
date: 2005-04-18
forum: Networking &amp; Wireless
---

### Post by jonny on 2005-04-18
I have a PC that I'm trying to use as a samba server.  It works well, but my client PC can't connect when Firestarter is running on the server.  Once a connection is established, I can restart Firestarter without losing the connection.  The Firestarter log shows no blocked events.

I've enabled the following ports for inbound traffic for my client device:

 - 137-139 SMB
 - 445 Microsoft-ds

I've also permitted connections from that host, but to no avail.  My outbound policy is permissive.

Does anyone have a working configuration that I can crib?

---

### Post by Boomgawd on 2005-04-19
not sure why, but for me I had to check the "share intenet connection' in firestarter.. after that it work.. before I check that box, everything worked but samba.. 

not sure if this is your problem, but worth a try.

Boom.

---

### Post by jonny on 2005-04-19
Enlightenment at last.  I found the solution [here](http://ubuntuforums.org/showthread.php?t=24440&page=1&pp=10) .

---

