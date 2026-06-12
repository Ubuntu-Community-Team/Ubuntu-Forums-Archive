---
title: "Wired network drops; Dell poweredge 2800"
date: 2015-03-18
forum: Networking &amp; Wireless
---

### Post by dixon2 on 2015-03-18
Hey Guys,

I recently installed on a PE 2800 server and am having trouble keeping the network up so i may use it headless.

After a time, the connection seems to drop which is odd as looking at my LAN switch and controller on the board, both show activity and link lights. 

Looking at the logs, Network Manager is not saying much before dropping the connection but i knew it to cause problems. I disabled it, put a static entry into /etc/network/interfaces and tried that out. 

Still nothing i'm afraid, the connection still drops after about 30 mins idle. 

The Ubuntu version is 14.10

wired connection is as follows

[FONT=sans-serif]Dual embedded Intel 10/100/1000 Gigabit NIC, Intel PRO/1000 MT Gigabit [/FONT]
NIC (copper)


Appreciate your help,
Dixon

---

### Post by tgalati4 on 2015-03-19
I would put a Fluke network meter on your cabling.  Make sure your crimps are correct and that you are getting at least Cat5e speeds (350 MHz bandwidth).  How old is the 2800?  It's possible there is a problem with the motherboard like bad capacitors.  I would boot a live 14.04 desktop or server edition and run that for a while and see if the network stays up.  It could be a kernel version issue.

---

