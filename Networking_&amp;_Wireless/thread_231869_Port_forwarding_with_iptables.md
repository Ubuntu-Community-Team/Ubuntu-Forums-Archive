---
title: "Port forwarding with iptables"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by VodaVoda on 2006-08-07
Hi guys

Hope I m posting in the right place :p 

I have two machines say A & B.

Both are in school LAN but A got an external WAN IP assigned
and B got an internal LAN IP only. There is only 1 ethernet card
on each machine.

I tried to map one port from A to B so that I can host a
FTP service on B. ( Remind that A is not the gateway of B,
they are both in a big LAN )

So what should be the right steps to do?

I tried the following commands:

1) [COLOR="Blue"]iptables -t nat -A PREROUTING -p tcp -d [COLOR="DarkRed"]AAAAA[/COLOR] --dport [COLOR="Green"]1234[/COLOR] -j DNAT --to [COLOR="DarkRed"]BBBBB[/COLOR]:[COLOR="Green"]1234[/COLOR][/COLOR]
2) [COLOR="Blue"]iptables -t nat -A POSTROUTING -d [COLOR="DarkRed"]BBBBB[/COLOR] -p tcp -m tcp --dport [COLOR="Green"]1234[/COLOR] -j SNAT --to-source [COLOR="DarkRed"]AAAAA[/COLOR][/COLOR]

AAAAA = IP address of A
BBBBB = IP address of B
1234 = port number ( the same for A & B)

I tried 1) only. It doesnt work. ( It works if I map A -> A. )
I tried 1) + 2). Doesnot work as well.

All default policies are ACCEPT.
And I am sure 1234 of B is listening.

Really Thanks for any help

---

### Post by VodaVoda on 2006-08-08
bump bump

---

