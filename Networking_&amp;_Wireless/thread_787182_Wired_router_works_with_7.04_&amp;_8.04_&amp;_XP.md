---
title: "Wired router works with 7.04 &amp; 8.04 &amp; XP"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Glugglug on 2008-05-08
I have a problem with my Netgear DG 632 router it would never work with Gutsy 7.10 or Mint 4.0 and I tried it today with Mandriva and its just the same it detects the connection and everything looks ok and I can access the router control panel  everything appears to be correct but I can't load web pages . If I unplug the Ethernet cable and plug in a computer running 7.04 or 8.04 or XP it works no problem .

---

### Post by superprash2003 on 2008-05-08
in the terminal type ping google.com or ping 64.233.167.99 and post output here

---

### Post by Glugglug on 2008-05-09
[attach]69353[/attach]       7.04 that works

[attach]69354[/attach]        7.10 doesn't load web pages

---

### Post by superprash2003 on 2008-05-09
try opening [http://64.233.187.99](http://64.233.187.99) which is google's ip.. and see if it opens in firefox.. if it does then i guess its a dns problem

---

### Post by Glugglug on 2008-05-09
> **superprash2003 said:**
> try opening [http://64.233.187.99](http://64.233.187.99) which is google's ip.. and see if it opens in firefox.. if it does then i guess its a dns problem

Yes it opens in Firefox and I did a search for Ubuntu forums but just clicking on the links wont open anything.

---

### Post by superprash2003 on 2008-05-09
its mostly a DNS issue.. try changing your DNS servers to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

