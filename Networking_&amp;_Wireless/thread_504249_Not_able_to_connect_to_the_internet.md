---
title: "Not able to connect to the internet"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by JenniferE on 2007-07-18
[color=indigo]I've been running Linux for a few months now without any trouble. Earlier today, I could connect to the internet with no problem.  I rebooted because my system had completely locked up due to me running too many things at once. Since reboot, I can't connect to the internet and I can't see any of the other computers on the network. 

I read a post about the network settings and made sure mine was set to what was suggested. Then I opened a terminal and did the ping -c2 127.0.0.1 and ping -c2 72.14.207.99 tests. No errors appeared. Then I tried ping -c2 google.com and I got the unknown host google.com error. 

The internet cable is plugged into my computer. The router, (Dlink Wireless Dl-524), and modem are running fine. All the other computers are running smooth. 

I'm pretty new to all of this and I'm a bit at a loss. I'd appreciate any help. 

Thank you!
:) [/color]

---

### Post by scrooge_74 on 2007-07-18
Ping your router IP address for a start

The IP of google is 208.69.32.230, ping the IP not the name that way you can check if the problem is with name resolution (DNS servers)

type ifconfig and post the results on your card

check that you did not lose your DNS servers address

edit: I just check the IP you were pinging and it is a google address.  Ping the router then, it could be a DNS related issue, check opendns.com website and get the DNS servers there and the howto on how to keep them even after a reboot

---

### Post by kevdog on 2007-07-18
Sounds like a DNS issue to me.  Can you post your /etc/resolv.conf and /etc/dhcp3/dhclient.conf, and /etc/hosts files??

---

### Post by JenniferE on 2007-07-19
[color=indigo]Hi Guys!  I appreciate the help. :) It seems as though my router was having an attitude problem and decided to act up last night. (I believe it was a DHCP issue)  This morning, everything seems back to normal. I appreciate your time guys.

Thanks again!
:) [/color]

---

