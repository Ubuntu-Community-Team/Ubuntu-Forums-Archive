---
title: "Ruoter WWW problems"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by RudolfMDLT on 2006-12-27
Hi guys,

I have a Holiday job that involves configuring and installing of mikrotik routers. I´m still learning the ropes - Right now these things have driven me up the wall and I´m desperate for a little help.

The router acts as an Access point/Bridge between Ethernet, Wifi and a 3G-HSDPA card. Getting internet access clients usually works but now I´m stuck. When I ping a website, i get the following:

ping ubuntuforums.org
PING ubuntuforums.org (82.211.81.186) 56(84) bytes of data.
time out
time out
time out

And when i try to open the website through a browser the browsers(I´ve tried a couple) all return with a message that the website timed out or cannot be displayed - Nothing about that page cannot be displayed or the website was´t found.

Noe the question - What do you think can cause a PC to ¨see¨ a website, to resolve the URL to an ip but be unable to open or ping. What on the router will not allow the traffic through. For the record the 3G connection is a PPP connection.


Your help will really be appreciated,

Rudolf Hoehler

---

### Post by dbott67 on 2006-12-27
There are a number of people that are having issues with off-brand routers and name resolution.  You may want to try 2 things:

1. Blacklist ipv6
2. Change default DNS servers to OpenDNS servers.

Both steps are outlined in this thread (post #3 and #5):

[http://www.ubuntuforums.org/showthread.php?t=323747 ](http://www.ubuntuforums.org/showthread.php?t=323747 )

-Dave

---

### Post by RudolfMDLT on 2006-12-27
Hi,

Just 2 quick things,

1) I know it ain´t a Linux/Ubuntu related question but these forums have become a real source of over flowing information and the members have mostly been able to help with anything!

2) I am no Rocket scientist so I don´t expect complicated answers - Please, any help in any form or magnitude will really be appreciated! i really need to know what is going on with this!

Thank you very much,

Rudolf

---

### Post by dbott67 on 2006-12-27
Did you try my suggestions above?

---

### Post by RudolfMDLT on 2006-12-28
dbott67.

It appears that I posted my second post simultaneously with your reply. 

I checked last night and the problem isn´t just Ubuntu related - All the machines - Windows and Ubuntu alike, even a Skype WiFi phone have this problem. It must be to do with the router. Any other ideas - It does seem that you are very knowledgeable about this area. What in a router can cause this?

Anybody else who think they have an idea?(I would appreciate it if you do;) )

Thanks,

Rudolf

---

