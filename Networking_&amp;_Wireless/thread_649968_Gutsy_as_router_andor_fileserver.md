---
title: "Gutsy as router and/or fileserver?"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by guhpraset on 2007-12-25
I am planning to use Ubuntu 7.10 desktop as router, and maybe as fileserver for 9 workstations with Windows XP. The shared printer will attached on one of the workstation.  

Do you think this is good idea? May i have the step by step tutorial?

I like gutsy because it is linux i most familiar with. Thankyou.

---

### Post by mightyteegar on 2007-12-26
First, you CAN use Linux as a router, but it's not overly easy to set up.  Here are some things to consider before trying this:

+ You'll need at least two NICs to make it work.  Do you have at least two?
+ Do you already have another router on your network?  If so, you'll very likely want to disable it.  
+ You will need to be or become familiar with packet forwarding using iptables.  

Second, setting up a Linux box as a file server is pretty simple.  You'll need to install Samba server and configure shared resources (directories and the printer), and there are many excellent tutorials available that can help you do this.  Studying /etc/samba/smb.conf will help you learn how to create Samba shares as well.  

Finally, I would STRONGLY advise against using a machine as both a router and file server.  Routers need to be able to route packets extremely quickly, which means the hardware needs to be dedicated to routing; anything else eating up processor time and memory is going to degrade a router's performance.  My advice would be to just use a dedicated router and use your Linux machine as the file server.  

I can help you with Samba if you need me to.

---

