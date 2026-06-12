---
title: "dhcp server and iptables"
date: 2019-06-11
forum: Networking &amp; Wireless
---

### Post by webmiester on 2019-06-11
hi everyone,

I hope this doesnt sound like a stupid question... I had this idea for my network...

I have a server which I protect by using IPtables.  It basically rejects everything outside a specific range.  Lets say, it only allows communication with those with IP of xxx.xxx.xxx.1 to 10...

There are a lot of other computers in the network outside this range.  If I use this same server as the DHCP server for the network...  Will it work to give IP addressess to computers outside this 1 to 10 range, or will the IP tables prevent those computers from getting their IPs?

I hope the question doesnt sound so vague. 

I ask this because I am trying to see if I can save some money and setup resources by using the same server for DHCP and another application, and still provide security to the other application through IP tables.  Thank you.

---

### Post by SeijiSensei on 2019-06-12
You will have to accept all traffic to the broadcast address, 255.255.255.255 on UDP ports 67 and 68.

```

/sbin/iptables -A INPUT -d 255.255.255.255 -p udp --dport 67:68 -j ACCEPT

```

DHCP operates via broadcasts. A client sends its request to the broadcast address. The DHCP server intercepts and processes the request.  The address the client receives doesn't matter in this transaction.

---

### Post by Doug S on 2019-06-12
> **SeijiSensei said:**
> You will have to accept all traffic to the broadcast address, 255.255.255.255 on UDP ports 67 and 68.

```

/sbin/iptables -A INPUT -d 255.255.255.255 -p udp --dport 67:68 -j ACCEPT

```

DHCP operates via broadcasts. A client sends its request to the broadcast address. The DHCP server intercepts and processes the request.  The address the client receives doesn't matter in this transaction.Seiji, I disagree. As far as I can tell, yes, they broadcast when they don't know anything, but thereafter and for renewals, they use the actual addresses. Even though I have static IP addresses, my ISP still makes me get them via DHCP (i.e. I just always get the same IP addresses).

On my external network, there is never a broadcast address involved (however it needs to be noted that my tcpdump capture stuff is never running on that server during boot). On my internal network, serviced by my DHCP server, I do see both broadcast and not broadcast involved. Examples:

```
2019-03-12 06:16:21.514034 IP 192.168.111.112.68 > 192.168.111.1.67: BOOTP/DHCP, Request from f4:6d:04:65:2d:8e, length 300
2019-03-12 06:16:21.514276 IP 192.168.111.1.67 > 192.168.111.112.68: BOOTP/DHCP, Reply, length 300


2019-03-12 14:14:01.367364 IP 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from b8:27:eb:12:14:a0, length 334
2019-03-12 14:14:01.367658 IP 192.168.111.1.67 > 192.168.111.118.68: BOOTP/DHCP, Reply, length 300
```

Anyway, I have been using this in my iptables rule set for many years now:

```
#
# DHCPd - Enable the following lines if you run an INTERNAL DHCPd server
#
# Smythies: Is not only the udp line required? There will never be tcp for this.
#$IPTABLES -A INPUT -i $INTIF -p tcp --sport 68 --dport 67 -j ACCEPT
$IPTABLES -A INPUT -i $INTIF -p udp --sport 68 --dport 67 -j ACCEPT

```

---

### Post by SeijiSensei on 2019-06-12
If his firewall blocks access from a client's current IP address outside the permitted range, I'm pretty sure the client would fall back to a broadcast. 

He could also use your rule that relies on the interface name which then accepts traffic from any IP on port 67.  It's the equivalent of "-i $INTIF -d 0.0.0.0".

---

