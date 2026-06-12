---
title: "ip traffic routing"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by zxiion on 2006-10-25
hello, im kinda of new to asking questions on forums, but ill give it a shot... i have the need to be able to block internal computes on a network access to the internet the gateway is going to be a linux box with 2 nics in it and i was wondering if there was a way to on the fly, block an ip range while allowing other ips access to the internet is there a way to do it in ipchains or ip route i still want it to be able to talk to the gateway to get an ip address i just dont want it to be able to communicate with the outside world.... and that leads me to another twist is there a way to allow it access to say one specfic ip on the internet but no others?

thanks..

---

### Post by adwait on 2006-10-25
You can do all of these things by configuring the Iptables on the gateway computer. Check the man pages of ip tables with
```
man iptables
```
for complete information about the command.

---

### Post by zxiion on 2006-10-26
thanks... last nite i also figured out u can use ipfw to filter the traffic as well.... i have a nother question but its more hardware based and programming based this all relates to a project im working on is there a way with a modem or something to be able to see how many pages were sent in a fax... like hook a fax machine up to a modem line port and have the modem intercept the data to see how many pages are in a fax... i think this is going to be the hardest thing to do

---

