---
title: "Remote access to LAN"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by minghai on 2007-01-01
Hi all,

     I've setup a LAN in my office with 4 Ubuntu 6.10 machines.  They are all connected to a router and get their IP addresses via DHCP.  How can I access them from home to manage them and install new software?  Most of the solutions I've come across seem to require my office machines to have static IP addresses.  I have a dual boot WinXP/Ubuntu 6.10 desktop at home.  If someone has done something similar, I'd be most grateful for any help or advice.  Thanks!

Ming Hai

---

### Post by kidders on 2007-01-01
Hi there,

That depends on your router. See if it can redirect incoming traffic on certain ports to a specific DHCP client. Assuming it can, you could perhaps run an SSH server on one of your machines. As you mentioned, some routers are too dumb to handle NAT with dynamically assigned IP addresses ... if yours is one of them, you can just configure it's network connection manually.

---

### Post by minghai on 2007-01-01
Hi kidders,

    Thanks so much for your reply.  I'll go into the office tomorrow and find out what router I'm using.  I'm kinda new to all this network stuff, do you have any pointers to docs on redirecting incoming traffic on certain ports to a specific DHCP client or on configuring it's network connection manually?  Thanks!

Ming Hai

---

