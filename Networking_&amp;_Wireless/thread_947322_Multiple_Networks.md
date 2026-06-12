---
title: "Multiple Networks"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by jazen on 2008-10-14
I'm having a problem getting my computer to connect to 2 networks at once. Basically, my PC will connect to wireless and Ethernet (separately) but not at the same time and my laptop isn't connecting to wireless, but will work with a wired connection.  So how do I get my PC to connect to the wireless while also connecting to the laptop?

---

### Post by Archmage on 2008-10-14
You need to configure what route needs what connection.

---

### Post by Iowan on 2008-10-14
It's possible you need to set up **/etc/network/interfaces** file to automount both (Network Manager reportedly will not set up both).

---

