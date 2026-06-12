---
title: "I can the see the Network, but i can't connect."
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by Bl3w on 2008-02-09
Hey guys
First, sorry for my bad english.

I just installed ubuntu yesterday (noobie lol), the problem is that i can't connect to a  wireless network.
I can see the network's, but when i try to connect to one (encrypted or not encrypted) the connection "hangs" 2 or 3 minutes, and then, it goes back to the password insert/definitions window.
I also tried wifi-radar, and the problem continues.

Help me please, i really want leave Windows. :)

/Edit: Bad title, upzz. :$

---

### Post by Bubba64 on 2008-02-10
If your trying to connect to random networks the signal can change and not hook up on my very old laptop if the signal is less than 10% I can't connect. You might include the Ubuntu program you installed the, and computer and wireless card your using for a more prompt response It may also be that if it is not your own network. what you think isn't locked actually is.

---

### Post by GSF1200S on 2008-02-10
Please post the results of the following commands run in a terminal (you have ethernet for connecting, right?)

lspci

ifconfig

iwconfig

---

### Post by FrankVdb on 2008-02-10
Older laptops indeed have weaker signal reception.

Try to get as close t a router as possible and see whether you can connect. If the network is using a security key, you will have to enter it. Without the key, you will see the network but you won't get a connection.

---

