---
title: "Relakks VPN &amp; Firestarter"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2007-11-14
Has anyone managed to get the Relakks VPN working while Firestarter is running? How would one go about doing that?

---

### Post by 1/0 on 2007-11-14
I've gotten it to work on a workstation without firewall but not on a server with pptp... This might help though:

[http://forum.piratpartiet.se/Topic64139-164-1.aspx](http://forum.piratpartiet.se/Topic64139-164-1.aspx)
[http://gentoo-wiki.com/Relakks](http://gentoo-wiki.com/Relakks)

Basically GRE TCP packets has to be let through on port 1723

---

### Post by PartisanEntity on 2007-11-14
A bit confusing, I shall have to read through the links a couple times. I set up Relakks through Network Manager, this worked and was quite easy to set up. Also I did it all using the GUI, so all this command line talk is a bit confusing since I did not set it up using command line (not that I mind, it's just that I cannot relate to most of it, sounds like gibberish to me at the moment).

---

### Post by 1/0 on 2007-11-14
Is this a server or a router, i.e. is firestarter on the workstation or not? If its not a real firewall (instead a workstation) then you shouldn't have to mess more with relakks/network manager. You should only have to enable Relakks access via port 1723 (TCP) and GRE (protocol 47 is it?). I'd say you'd need to do something like this: 


```

iprelakks="ip.ip.ip.ip"
/sbin/iptables -N pptp
/sbin/iptables -A pptp -p tcp --destination-port 1723 --dst $iprelakks -j ACCEPT
/sbin/iptables -A pptp -p 47 --dst $iprelakks -j ACCEPT
/sbin/iptables -I FORWARD -j pptp
/sbin/iptables -t nat -N pptp
/sbin/iptables -t nat -A pptp -i $RED_DEV -p tcp --dport 1723 -j DNAT --to $iprelakks:1723
/sbin/iptables -t nat -A pptp -i $RED_DEV -p 47 -j DNAT --to $iprelakks
/sbin/iptables -t nat -A PREROUTING -j pptp

```

But I don't use a firewall on my workstation so I'm not that good on firestarter...

---

### Post by PartisanEntity on 2007-11-14
Yes Firestarter is on the workstation i.e. my laptop.

Concerning the example you posted, the IP is always different when I connect to Relakks though.

---

### Post by coldstatue on 2008-01-31
i'd like to know a simple solution wihin the fs gui as well. i followed the instructions at
[http://www.fs-security.com/docs/vpn.php](http://www.fs-security.com/docs/vpn.php)
i also allowed service on 1723, but no luck. i have to shut off the firewall to use relakks.

---

### Post by PartisanEntity on 2008-01-31
After I deinstalled Firestarter it worked hassle free.

---

