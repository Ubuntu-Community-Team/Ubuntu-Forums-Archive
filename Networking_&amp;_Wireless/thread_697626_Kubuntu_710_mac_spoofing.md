---
title: "Kubuntu 710 mac spoofing"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by lordrayden75 on 2008-02-15
Hi, I got myself a new pc, I put Kubuntu on it, but I have to spoof my mac address to get online. It works with "ifconfig ... hw ether ...", but i can't make it last through a reboot.
 I tried altering the etc/network/interfaces and still nothing.
 I did the same thing on Debian etch and it worked.
 Any ideas what's the problem?
 
 P.S. It's the first time I use any *buntu, I sticked with Debian till now, so I thought maybe there's smth I don't know yet.

---

### Post by Lars Noodén on 2008-02-16
Maybe as a work-around, put it into /etc/rc.local so that it gets run at start up.  Just don't forget it's there.  Can't you change ISP's?

---

### Post by lordrayden75 on 2008-02-17
I dunno how it's done, i tried macchanger, then I quit trying, but in the end it seems there is no need for special tweaking in this version. My eth0 still displays the original MAC, but my internet is working like a charm.
I just did the traditional ifconfig .. hw ether ..
Strange, but if it works...

---

