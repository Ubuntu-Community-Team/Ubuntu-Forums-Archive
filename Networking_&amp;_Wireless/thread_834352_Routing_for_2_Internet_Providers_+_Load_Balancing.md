---
title: "Routing for 2 Internet Providers + Load Balancing"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by beckols on 2008-06-19
I have a server with 3 NIC's, 2 for separate DSL links, 1 for the LAN.  I need to make use of both of the lines, and I need load balancing.  I understand the general gist of how to do it, although I haven't tried it yet.  So please don't direct me to [Routing for Multiple Uplinks/Providers]("http://lartc.org/howto/lartc.rpdb.multiple-links.html")

My problem is that I get dynamically assigned IP Addresses, and that document only tells you how to do it with static IP addresses.  Does anyone know how I can get it to work with static IP addresses??

I was going to make a script that would use [curl]("http://curl.haxx.se/") to retrieve my ip from whatismyip.org, but that won't work because if it is set up correctly it will choose a random interface to send the request, so I could end up with either IP Address.

---

### Post by .chaos on 2008-06-19
here's how to setup ubuntu for dynamic ip's

[http://www.nukesilo.com/2007/03/19/configuring-dhcp-addressing-for-ubuntu-linux/](http://www.nukesilo.com/2007/03/19/configuring-dhcp-addressing-for-ubuntu-linux/)

i'm guessing you would make two entries in the config, one for each adapter.  you might be able to make one entry seperating the info by commas but i'd prolly go with the two entry idea.  i'm guessing there's another conf file somewhere that you would then bring those two devices you setup with that link into play.

load balancing is on you. can't help you there.  

i'm very new btw so i could be off but it might be worth a try.

---

### Post by beckols on 2008-06-19
haha yea, just a little off.  I know how to set static IP's in ubuntu, but I need a static IP from my ISP, which I can't change.  I might call them up and see if I could get a static IP from them, but I would only do that if it was free.

---

### Post by beckols on 2008-06-19
bump

---

### Post by beckols on 2008-06-20
Well the solution was pretty simple, I just didn't take time to think about all my options.  An ifconfig will retrieve the IP addresses of both of the interfaces with a little help from awk.  If anyone is interested, this is part of the script I used to get both IP addresses into variables:

```
IP1=`ifconfig | awk -F: '/71.98./ {print $2}' | awk '{ORS=" "; print $1}' | awk '{print $1}'`

IP2=`ifconfig | awk -F: '/71.98./ {print $2}' | awk '{ORS=" "; print $1}' | awk '{print $2}'`
```

Ok, so I have those, now here is my next problem.  the `ip route` command needs my ISP's gateway address, but in one article I saw that it really just needs your first hop destination so it could be just my dsl modem... could anyone clarify this for me?  When I do a tracepath, there are 3 lines with a "1:" in front of them, and the first one is my external IP Address, the other two are the exact same, and they are the gateway of the ISP... which do I use??

---

### Post by intermod on 2009-11-13
Its 2009, and you likely solved your challenge. But I am just now trying this, but with two internal nets, to force each internal nets through a different external interface.  Not tried yet, but I think you need the ISP's (or cable modem/DSL router) gateway address. You can run this:
 
      ip route list table main

from:
[http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.rpdb.simple.html](http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.rpdb.simple.html)

The last line indicates the gateway of the modem in the ISP's network.  Mine looks like this (only one external interface for now):

192.168.0.0/24 dev eth1 scope link
67.175.248.0/22 dev eth0 proto kernel scope link src 67.175.250.109
169.254.0.0/16 dev eth2 scope link
10.0.0.0/8 dev eth2 scope link
127.0.0.0/8 dev lo scope link
default via 67.175.248.1 dev eth0
  
It is  67.175.248.1.

Cable modem's IP is 67.175.250.109, and its part of the 67.175.248.0/22 net. 

I just need to find which file this gateway IP address resides in, and prepare a script to get it out.

---

