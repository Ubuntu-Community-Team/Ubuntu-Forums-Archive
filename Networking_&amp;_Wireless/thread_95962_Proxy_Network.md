---
title: "Proxy Network"
date: 2005-11-27
forum: Networking &amp; Wireless
---

### Post by acheun on 2005-11-27
Just installed Breezy Badger in a P3 box.  I intent to use this box act as a firewall and proxy server.  This box is attached with a ADSL modem/router via a primary network card.  There is a 2nd network card and connect to local LAN.  All the set up looks OK, eth0 and eth1 are reported to be working.  The  P3 box can access internet without problem.  All boxes can see each others.  

The problem is other than the P3 box, none of other boxes in the LAN able to see the internet.  When I try to ping the ADSL modem/router, it just not response, it just hang there, not even any error message shown.

The setting is like this: 
In P3 box, 
eth0 address: 192.168.1.0
netmask: 255.255.255.0
gateway: 192.168.1.254

eth1 address: 192.168.5.1
netmask: 255.255.255.0

In all boxes in LAN:
eth0 address: 192.168.5.*
gateway: 192.168.5.1

Is there any configuration I missing or gateway set up I need to do?

---

### Post by mindwarp on 2005-11-28
Your p3 box cannot have an address of 192.168.1.0.  Valid addresses are 192.168.1.1 - 192.168.1.254.  192.168.1.1 is generally reserved for the router.  Also with a netmask of 255.255.255.0, the systems can only see other systems on ips of 192.168.5.*, 192.168.1.* does not exist to them.  I suggest a network redesign is in order, and unless you have a good reason to use a proxy server just setup a firewall that does nat.  Plenty of tutorials.

---

### Post by cwaldbieser on 2005-11-28
[QUOTE=acheun]Just installed Breezy Badger in a P3 box.  I intent to use this box act as a firewall and proxy server.  This box is attached with a ADSL modem/router via a primary network card.  There is a 2nd network card and connect to local LAN.  All the set up looks OK, eth0 and eth1 are reported to be working.  The  P3 box can access internet without problem.  All boxes can see each others.  

The problem is other than the P3 box, none of other boxes in the LAN able to see the internet.  When I try to ping the ADSL modem/router, it just not response, it just hang there, not even any error message shown.

The setting is like this: 
In P3 box, 
eth0 address: 192.168.1.0
netmask: 255.255.255.0
gateway: 192.168.1.254

eth1 address: 192.168.5.1
netmask: 255.255.255.0

In all boxes in LAN:
eth0 address: 192.168.5.*
gateway: 192.168.5.1

Is there any configuration I missing or gateway set up I need to do?[/QUOTE]
As mindwarp mentioned, the 192.168.1.0 address is reserved.  I don't see where your netmask is a problem, though.

By default, Ubuntu is not set up to do IP forwarding.  If you type:
```

$ cat /proc/sys/net/ipv4/ip_forward

```
You will either get a 1 or a 0 as a result.  0 means IP forwarding is turned off, and your machine won't act as a router.

I forget where you set this, offhand, but it is probably in /etc/network somewhere.  A quick forum search should turn up the answer.

---

### Post by acheun on 2005-11-28
Thanks for pointing it out.  It's a typo mistake.  I want the address to be 192.168.1.1.  My ADSL router is set as 192.168.1.254 as default, so I keep it this way.  I made the change and it still didn't work.  

So I do some research. And I find a Debian tutorial site for beginner, which suite me well.  It demonstrate how to run a proxy. I got a sample script from it.  After I adjust some IP address as stated in the script.  I finally got it works.  Really happy about it. 

Though it has a bit of learning curve, I find it's still easy.

For any one who interests,, pls refer to this: [http://www.aboutdebian.com/proxy.htm](http://www.aboutdebian.com/proxy.htm).

---

### Post by mips on 2005-11-28
[http://ubuntuforums.org/showthread.php?t=89320](http://ubuntuforums.org/showthread.php?t=89320)

---

