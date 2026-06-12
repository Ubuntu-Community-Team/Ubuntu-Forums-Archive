---
title: "Problems with ip forwarding"
date: 2005-06-19
forum: Networking &amp; Wireless
---

### Post by blixel on 2005-06-19
I'm trying to use my laptop as a quick and dirty router for another machine I have.

My laptop has a wireless connection and a 10/100Mb Ethernet port.  The IP address of my laptop's wireless card is 172.16.1.12.  The default gateway for my laptop is 172.16.1.1.  Everything on the laptop is working just fine with regards to Network/Internet connectivity.

I want to plug in my other machine to my laptop's wired Ethernet port (via a cross over network cable) and be able to access the Internet from that other machine.  This seems like it would have been a simple thing to do but I can't make it work.

I statically assigned 192.168.100.1 to my laptop's Ethernet port.

I statically assigned 192.168.100.2 to my other machine and set 192.168.100.1 as the default gateway.

Those two machines are able to ping each other's 192.168.100.x address.  (So that tells me the cross over cable is working at least.)

I then ran:

```
echo "1" > /proc/sys/net/ipv4/ip_forward
```

on my laptop to enable ip forwarding.  I also checked the iptables to make sure there wasn't any kind of port blocking.

```
iptables -L
```

The iptables command showed that everything was open.

At that point, I expected to be able to ping the laptop's default gateway (172.16.1.1) from the 192.168.100.2 machine.  I had not yet setup my /etc/resolv.conf on the 192.168.100.2 machine so I knew I wouldn't be able to ping host names yet.

This is where I'm stuck.

From the 192.168.100.2 machine I can ping the IP address of the laptop's **wired** port (192.168.100.1), and I can ping the IP address of the laptop's **wireless** card (172.16.1.12).  However, I can not ping any other machines on the network, nor can I ping the local router (172.16.1.1).

What am I missing?  Since I'm working with private IP space only, I wouldn't think I would need any kind of IP masquerading.  I'm thinking at most, I need 1 or two rules for iptables for the forwarding.  But I'm not sure what that would be.

---

### Post by sksbir on 2005-06-19
you had the anwser : just looking for "masquerade" threw the forum : take a look at here : [http://ubuntuforums.org/showthread.php?t=42769](http://ubuntuforums.org/showthread.php?t=42769)

---

### Post by blixel on 2005-06-20
[QUOTE=sksbir]you had the anwser : just looking for "masquerade" threw the forum : take a look at here : [http://ubuntuforums.org/showthread.php?t=42769](http://ubuntuforums.org/showthread.php?t=42769)[/QUOTE]

Ah ... thank you very much.  That 1 iptable rule was the last thing I needed.  I was thinking masquerading was only needed if you wanted to make a private IP address ([RFC 1597](http://www.faqs.org/rfcs/rfc1597.html) ) appear as a public IP address.

---

