---
title: "SCP between 2 machines with a router"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by alan888 on 2008-01-22
Hello:

I'am very new in the Linux world. I have a little problem with file transfer in network. I have 3 linux machines, A, B and C. A and B are in different private networks and C is a router between them.

In machine C, I have only 40MB of space, and I need transfer about 200MB of data between A and C. What can I do?. The problem is that I can't transfer files directly from A to B, I need pass for C machine.

I tray with scp, but is very slow.

Thanks

---

### Post by kirsche on 2008-01-22
You could use any other file transfer protocol, depenig on what services you have available on machine A (or whatever the target is) - ftp, cifs, http, nfs...
Just curious - what do you mean with slow?

---

