---
title: "Thompson speedtouch 510 connection refused"
date: 2005-07-09
forum: Networking &amp; Wireless
---

### Post by PaulWiggers on 2005-07-09
Hello,

I am still having problems with installing the speedtouch 510 ethernet modem. When I try to go to the webinterface of the modem (10.0.0.138 ) I get the message that the connection was refused. What does this mean? And more important how do i solve this problem?

---

### Post by sapo on 2005-07-09
you need to change your computers ip to 10.0.0.x otherwise you will never be abre to connect to you modem :p

btw.. if you have adsl connection just type pppoeconf in a terminal and you are online :p

to change your ip adress. go to

Applications -> System Tools -> Network Tools, select your network device (usualy eth0) and then click in configure  :-P

---

### Post by PaulWiggers on 2005-07-09
hello, thanks i will give that a try...but i have an dhcp connection (so no static ip) 
i have entered this option on my network card and tried the commands ifdown eth0 and ifup eth0 this shows me that my modems doesn't offer me a dhcp.

i have also tried the ppoeconf command but that gives me the message that no devices could be found.

i can give you the outcome of the ifup and ifdown commands if that will help.

---

