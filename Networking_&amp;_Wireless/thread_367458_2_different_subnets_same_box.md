---
title: "2 different subnets same box??"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by tiger.woods on 2007-02-22
I would like to run 2 different subnets on my server one for my local/private network and one for an external/public network.

Is this a feasable option and how would I go about doing on Edgy? Can someone give me some examples of what I would need to do this? Can I get one network card to recognize two different subnets or is it better to use 2 cards?

Thanks,

TW

---

### Post by Strider on 2007-02-22
You can use multiple IPs on a single NIC, however, in your case I would recommend using 2 NICs.

For multiple IPs on one NIC:
Assume eth0 is your current NIC and it has an IP of 192.168.3.100/24.  To create an additional IP you would enter the following from the terminal:

ifconfig eth0:0 192.168.5.100 netmask 255.255.255.0 up

This would create another interface using eth0 with IP 192.168.5.100/24.  You will also have to add the new interface to "/etc/network/interfaces".

Hope that helps.  Look up on google or on this site for "IP Alias" or "sub interfaces linux".

-Mike

---

### Post by tiger.woods on 2007-02-22
I think using 2 NICs is probably the way I'll go.

Are you familiar with how the DNS would setup on such a situation? I assume this really is the key to getting this working correctly?

Thanks,

---

### Post by gradedcheese on 2007-02-22
I do this on my file server, DNS stays the same (it's for resolving names afterall).  Buy two NICs, bring them up on different subnets, and you should be good to go.

---

### Post by tiger.woods on 2007-02-22
I recall a posting that I had read about a problem Windows has in handling a public/private subnet and routing - I think -  that Linux was not plagued with, does that ring a bell with you guy's? As to what that difference is?

TW,

---

### Post by Strider on 2007-02-23
Windows can share an Internet connection and with Windows XP you can setup two NIC - one public, one private - and have it share that connection.  I think Linux makes this a lot easier and you can use iptables to implement firewall rules between the two networks and also setup NAT if necessary.

I don't think you're run into any roadblocks on this.

---

