---
title: "problem with dual-network with multiple cards"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by MrPappy on 2008-10-18
Hi,

My set up is as follows:
100/10 ethernet connection to the internet. I get 5 dynamic IPs from my ISP and I get the 10Mbit/s upload on EACH IP. I want to use that of course.
I have an Ubuntu-LAMP-server with 5 NICs (4 to the ISP) and a dir-655 router with 2 computers (windows + kubuntu) behind it.
The ISP is limiting the upload at 10Mbit on it's network, and then that applies between my router and the ubuntu-machine (I do not get full GBit between them but want this).

I then have the eth0 in the server to hook into the LAN of my router to get away from this problem (I want a Gbit connection between server and desktop). I'm using IP-tables to protect the server from unwanted visits, with a looser policy on eth0.

Fine, it works like a charm.  I can connect on all NICs on the server from my windows desktop (eth0 LAN and the 4 cards connected to my ISP gate works perfectly).
My friends can connect to the 4 outer cards via FTP, Apache etc...

Problem: After awhile my friends cannot connect to the Ubuntu-server at all. 
I can still connect to the server via the eth0 and all the other cards from my desktop but they cannot.
If I detach the eth0 my friends can connect to the server on all outer NICs like normal.

I'm not a network-wiz and certainly not a linux-expert but why does this happen, and how do I solve it?

Any help would be great.

[img]http://pappy.homeip.net/bilder/pappy_lan_layout.gif[/img]

---

