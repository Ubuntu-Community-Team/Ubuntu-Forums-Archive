---
title: "How to connect remotely and get my files via the terminal?"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by endref on 2008-09-28
Hi

I have a home network. I want to access my files on my desktop computer (dual Vista and Ubuntu) with my laptop (Ubuntu) via the network.

I am able to connect via Terminal Server Client, but it is really slow. I only want to get my files, but I dont won't all my files being public to the whole network som I dont wont to make them all shared and access them via shared samba.


Is there a way to get to my files like a "terminal only version" of the Terminal Server Client from only the terminal or nautilus?


Thanks for any help on this.


- Endre

---

### Post by squaregoldfish on 2008-09-28
If you set up ssh, you can use the scp utility to copy files from one machine to the other using the command line.

There's plenty of info out there on setting up ssh, and it's written better than I can do it, so I'll leave that one to you :)

Steve.

---

