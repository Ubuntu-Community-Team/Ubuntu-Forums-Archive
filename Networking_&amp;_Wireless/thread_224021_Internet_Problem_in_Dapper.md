---
title: "Internet Problem in Dapper"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by meirbenezra on 2006-07-27
I think many people are having this problem internet not working after installation. Maybe it is better to keep this thread updated so its visible all the time... As for my specifications I use a ethernet dsl modem which sets up the ips and stuff by dhcp and ubuntu can realize the ip and other stuff of the modem but have some problems while recieving data from it because the network tools thing shows recieving errors which keep increasing all the time... anything else I should consider.

---

### Post by meirbenezra on 2006-07-27
pls unite all the similer problems here so the forum is not flooded with the same problem and everything scattered around... thx everyone...

---

### Post by mips on 2006-07-27
My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

