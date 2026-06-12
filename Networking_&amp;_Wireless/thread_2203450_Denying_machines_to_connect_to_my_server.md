---
title: "Denying machines to connect to my server"
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by Felhazi_Andrei on 2014-02-03
Hello, 

I would like to deny all connections to my LAN based on some kind of MAC whitelist.

Machines that don`t have their MAC address in a certain list should not be able to connect in any way to my server.

---

### Post by tgalati4 on 2014-02-03
MAC filtering is normally done in the router firmware.  What router are you using?

---

### Post by dargaud2 on 2014-02-04
In addition, on many systems there's nothing easier than changing the mac address: "ifconfig eth0 hw ether NEWMAC"

---

### Post by Felhazi_Andrei on 2014-02-04
[COLOR=#000000]my ubuntu 13.10 is a router. I do not use any other products except two gigabit switches and a wi-fi router, but that only acts as a wi-fi access point[/COLOR]

---

### Post by Felhazi_Andrei on 2014-02-04
I know that, but i doubt any of the 4th graders which try to connect to my server know that too.

---

### Post by SeijiSensei on 2014-02-04
Iptables lets you control access [via MAC addresses]("http://www.cyberciti.biz/tips/iptables-mac-address-filtering.html").  You write rules that key on the MAC rather than an IP address.  Here's an example from that link:
```
/sbin/iptables -A INPUT -m mac --mac-source 00:0F:EA:91:04:08 -j DROP
```
That drops all packets arriving on any interface from the machine with that MAC address.

If you only intend to permit a few machines and block all the others, it's easier to write rules like this:
```

/sbin/iptables -A INPUT -m mac --mac-source 00:11:22:33:44:55 -j ACCEPT
/sbin/iptables -A INPUT -m mac --mac-source 00:11:22:33:44:66 -j ACCEPT
/sbin/iptables -A INPUT -m mac --mac-source 00:11:22:33:44:FF -j ACCEPT
/sbin/iptables -A INPUT -j DROP

```

If this is your first time out with iptables, make sure you're seated at the console when you start writing rules.  If you're connected via SSH and make a mistake, you can be locked out of the machine. Been there, done that.

---

### Post by Felhazi_Andrei on 2014-02-05
Thank you! I have been working with iptables before but I did not know about this function. How do i specify the rules to work only on eth1? -o eth1?

---

### Post by Lars Noodén on 2014-02-05
It would be -i because you are filtering on the input.  The full name would be --in-interface, if you want to go for readability.  If you haven't already, take a look through the iptables manual pages and also the one for iptables-extensions.  It is the latter which has a mention of --mac-source and checking on the official reference is always helpful.  

At least while debugging your set up, you might want to use [REJECT](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/) instead of [DROP](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject).  I'd recommend doing that even after the rules are settled.

---

### Post by SeijiSensei on 2014-02-05
REJECT sends a packet back to the blocked machine informing it that access was denied.  In cases like the OP's those kinds of notices are simply overhead and DROP is more efficient.  I remember a posting by Linux networking guru [Alan Cox]("http://en.wikipedia.org/wiki/Alan_Cox") on the now defunct "server-linux" listserver where he expressed his glee about being able to "drop packets on the floor" that you don't want.  This was back when ipchains, the predecessor to iptables, was added to the kernel.

Also while you could add "-i eth1" to your rules, I don't see much point to it. If you are blocking by MAC, it shouldn't matter which interface the machine is connected to, should it?

---

### Post by Felhazi_Andrei on 2014-02-05
Thank you for your replies but when I try to add the rules I get the following error:

iptables: No chain/target/match by that name

---

### Post by Lars Noodén on 2014-02-05
Can you post the rules you are trying to add?  There is probably  be a typo in them.

---

