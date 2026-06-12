---
title: "How do I network these two desktops?"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by Sam3280 on 2008-10-01
Hi,
I have two desktop computers I want to network them so that the internet can be used on both at the same time.
I need to know what hardware I need. Currently I have an ADSL gateway with one Ethernet (RJ45) output and two desktop computers with Ubuntu Hardy Heron both desktops have one Ethernet port I also have an RJ45 double adapter. I also have a 10m cord and a shorter Ethernet cord.
Networking is for some reason my downfall so I need to know exactly what I will need. 
I want to know what hardware I need before I set the network up.
Thanks,

---

### Post by lisati on 2008-10-01
> **Sam3280 said:**
> Hi,
I have two desktop computers I want to network them so that the internet can be used on both at the same time.
I need to know what hardware I need. Currently I have an ADSL gateway with one Ethernet (RJ45) output and two desktop computers with Ubuntu Hardy Heron both desktops have one Ethernet port I also have an RJ45 double adapter. I also have a 10m cord and a shorter Ethernet cord.
Networking is for some reason my downfall so I need to know exactly what I will need. 
I want to know what hardware I need before I set the network up.
Thanks,

I'm not sure that a "double adaptor" (of a sort equivalent to what you'd use for electrical outlets) will be adequate - a router or switch to manage traffic on your home network will probably be a better idea.

An alternative to forking out for a switch/router/hub would be to connect the ethernet ports on your computers together - this normally needs a "crossover" cable - and to use a USB connection from one of your computers to the ADSL gateway if it supports it.

---

### Post by davidryder on 2008-10-01
Sounds like you just need a router. 

[http://www.amazon.com/Linksys-EtherFast-Router-4-Port-BEFSR41/dp/B00004SB92](http://www.amazon.com/Linksys-EtherFast-Router-4-Port-BEFSR41/dp/B00004SB92)[img]http://ecx.images-amazon.com/images/I/41MYKJ03NAL._SL500_AA280_.jpg[/img]

Alternatively you could purchase a second network card for one of the computers and bridge the connections. 

[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

IMO the router is the best route and definitely the simplest.

---

### Post by Herman on 2008-10-01
:D The previous posters are correct, but I'll elaborate a little bit more.
I'm not sure what you mean by a "an RJ45 double adapter" either. If you mean you have a switching hub with two ports in one side of it then you might be okay with that. 
I have a switching hub that only cost about $20 and can connect about eight computers together and to my ADSL modem-router if I want.
A router is a bit fancier than a switching hub because it has it's own very small simple Linux operating system in it which contains a firewall which you can configure to your needs.
Some people really like having the extra mini operating system and firewall. In some routers you can set who can access the internet and when and so on. 
You might also  want to have logs mailed to yourself so you can monitor traffic, (see any attempts to break in or unusual activity and so on).
You probably already have another mini operating system in your ADSL gateway as well, with another firewall in it too.
A router costs more, like maybe around $120 or more, and most of them now feature a wireless LAN in case you have a laptop and you might want to be able to carry it around the house and use it from any room.
You will need to least one cat5 cable (RJ45), to go from your ADSL modem-router to a switch or a router, and at least one more cat5 (rj45) cable from the switch or router to each computer.
(Unless you're planning on using wireless networking).

Here, click on this link and check out some of my illustrations, [Persistent SSH LAN]("http://users.bigpond.net.au/hermanzone/p11.htm#Persistent_SSH_LAN_").

That page is actually about Open SSH Networking, but it doesn't matter whether or not you care about OpenSSH, the equipment is still the same.
 [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm") Linux Home Networking... secure... user friendly... GUI...set up in minutes..!

---

### Post by Sam3280 on 2008-10-01
Thanks to all of you,
I feel like an idiot that I didn't think of putting a second network card in on of the computers, I think I have one in my spare parts drawer.
Thanks

---

### Post by davidryder on 2008-10-01
> **Herman said:**
> :D The previous posters are correct, but I'll elaborate a little bit more.
I'm not sure what you mean by a "an RJ45 double adapter" either. If you mean you have a switching hub with two ports in one side of it then you might be okay with that. 
I have a switching hub that only cost about $20 and can connect about eight computers together and to my ADSL modem-router if I want.
A router is a bit fancier than a switching hub because it has it's own very small simple Linux operating system in it which contains a firewall which you can configure to your needs.
Some people really like having the extra mini operating system and firewall. In some routers you can set who can access the internet and when and so on. 
You might also  want to have logs mailed to yourself so you can monitor traffic, (see any attempts to break in or unusual activity and so on).
You probably already have another mini operating system in your ADSL gateway as well, with another firewall in it too.
A router costs more, like maybe around $120 or more, and most of them now feature a wireless LAN in case you have a laptop and you might want to be able to carry it around the house and use it from any room.
You will need to least one cat5 cable (RJ45), to go from your ADSL modem-router to a switch or a router, and at least one more cat5 (rj45) cable from the switch or router to each computer.
(Unless you're planning on using wireless networking).

Here, click on this link and check out some of my illustrations, [Persistent SSH LAN]("http://users.bigpond.net.au/hermanzone/p11.htm#Persistent_SSH_LAN_").

That page is actually about Open SSH Networking, but it doesn't matter whether or not you care about OpenSSH, the equipment is still the same.
 [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm") Linux Home Networking... secure... user friendly... GUI...set up in minutes..!

You need something to direct traffic from the modem to the two computers. A switch will not do that. And routers without wireless costs <$40.

---

### Post by Herman on 2008-10-01
> You need something to direct traffic from the modem to the two computers. A switch will not do that. And routers without wireless costs <$40.:D Okay, well I don't know what kind of hardware you have, all I now is my switch does work perfectly well in my house for connecting as many computers as I want together and to the internet. Obviously there's some kind of a misunderstanding here.
I have a '[TP-Link TL-SF1008D]("http://www.tp-link.com/products/product_des.asp?id=80")', '8-port', '10/100M Fast Ethernet Switch', and that works just fine.
I agree that a router is better though.  we use a router now, and I lent my switch to a friend who is now using to connect all the computers in his house to the internet. :D

---

### Post by Iowan on 2008-10-01
If you have that second card, you might consider [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing").

---

### Post by davidryder on 2008-10-01
> **Herman said:**
> :D Okay, well I don't know what kind of hardware you have, all I now is my switch does work perfectly well in my house for connecting as many computers as I want together and to the internet. Obviously there's some kind of a misunderstanding here.
I have a '[TP-Link TL-SF1008D]("http://www.tp-link.com/products/product_des.asp?id=80")', '8-port', '10/100M Fast Ethernet Switch', and that works just fine.
I agree that a router is better though.  we use a router now, and I lent my switch to a friend who is now using to connect all the computers in his house to the internet. :D

Then that means your modem is capable of assigning multiple IP addresses. Switches don't assign IP addresses to computers on the network.

---

### Post by Herman on 2008-10-02
> Then that means your modem is capable of assigning multiple IP addresses. Switches don't assign IP addresses to computers on the network.:D Yes!  Now I see, there is a misunderstanding here, and it could be on my part.
I'm not certain what hardware the original poster has because it isn't stated, but here in Australia there are a lot of these around: [Alcatel Speed Touch 530 ADSL Residential USB Gateway-v4]("http://www.modem-help.co.uk/Alcatel/Speed-Touch-530-ADSL-Residential-USB-Gateway-v4.html") .
They are a modem-router, but the ones most home users only have a single port because Telstra Bigpond, our biggest ISP here in Australia, originally wanted an extra $100.00 (if I remember correctly), for the four port version.  An extra $100.00 sounded like a lot of extra money to me, for the same thing but just with an extra three holes.
So, we were better off buying the cheaper one and adding our own switch or router afterwards. That was a few years ago and I'm not sure what the current prices are like, possibly they have changed their pricing policies on routers with multiple ports. 
Perhaps I'm presuming too much in assuming that Sam3280 has the same ADSL gateway as I do, (with just a single port), just because we both happen to be in Australia. However, if Sam3280 has a multiple port ADSL gateway, it seems unlikely that he or she would be asking this question.

Have I interpreted the original poster's question correctly? Or did I jump to the wrong conclusion? :oops:

---

### Post by iponeverything on 2008-10-02
It sounds like you just want to NAT traffic thru your Internet connected box.

Add a second address to your NIC of the Internet connected box:

ifconfig eth0:1 172.16.1.1 netmask 255.255.255.0 

Make it NAT traffic:

echo 1 > /proc/sys/net/ipv4/conf/all/forwarding
iptables -t nat -A POSTROUTING -s  172.16.1.0/24 -j MASQUERADE

The machine that wants to get out through the Internet connected box:

ifconfig eth0 172.16.1.2 netmask 255.255.255.0 gw 172.16.1.1

and your good to go.

---

### Post by davidryder on 2008-10-02
> **Herman said:**
> 
Have I interpreted the original poster's question correctly? Or did I jump to the wrong conclusion? :oops:

No! I think it was just a simple misunderstanding. I myself didn't even think about the modem being able to assign multiple IP addresses so you bring up a good point. It's very possible he won't need a router... I guess it just depends on his hardware. :)

---

### Post by Sam3280 on 2008-10-03
Just to clear things up. I will put a second network card in the computer near the ADSL gateway, I should be able to have a network between the two computers and they should be able to have the same internet connection is that right? (thanks to everybody who has answered)

---

