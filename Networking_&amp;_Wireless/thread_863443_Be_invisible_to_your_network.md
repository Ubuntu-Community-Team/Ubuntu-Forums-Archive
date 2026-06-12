---
title: "Be invisible to your network?"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by dominicx1889x on 2008-07-18
I noticed on another computer in my home network(windows xp) that there's a program called "Network Magic" running; it displays everybody on the router and has time logs of when anybody on the network logs on or logs off. I was wondering if there's anyway with Ubuntu or any other distribution of linux to make your self *invisible* to the network such that the program cannot see me on the network. This is for my own security reasons.

---

### Post by jimv on 2008-07-18
I'm going to say no, because once you plug into a network, your machine will announce itself via mac address to the router to get an IP.  Any other machines on the network will see these announcements too.

You can't be on the network and not on the network at the same time.

---

### Post by pseudo-random on 2008-07-18
Learn about arp spoofing. It won't help you 'hide' but it will give you a good understanding of why you cannot.

---

