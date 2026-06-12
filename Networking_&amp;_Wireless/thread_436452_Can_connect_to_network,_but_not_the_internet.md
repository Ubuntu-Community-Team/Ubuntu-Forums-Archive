---
title: "Can connect to network, but not the internet"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by waterskier357 on 2007-05-07
Hey guys.  I'm new to Linux and Ubuntu, and need a little help.  I can connect to my wireless network fine, but I can't access any websites.  What should I do?

My wireless card is a Netgear WPN311.

---

### Post by dante.regis on 2007-05-07
did you connected to the internet while using windows? if you did, how did you do that? You were always connected or had you to run a dialer, or any other program?

---

### Post by Arseniy FreeAtNet on 2007-05-08
I had a kind of this problem on D-Link T604 ADSL Access Point, Netgear WG511v2 and a fresh installation of Ubuntu 6.06. While the network was connected, IPs were reachable, but not the domain names.
It turned out that I had the AP set to relaying DNS automaticly, but it did not (at least not the way Ubuntu got it).
So I had to go to Network Configuration manager and set DNS servers manually. I used 212.188.4.10 and 212.188.4.10, but these are local (russian) and it can take a longer time to work with them

---

