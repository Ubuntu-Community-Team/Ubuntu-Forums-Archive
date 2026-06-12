---
title: "IPv4 or IPv6"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by Willye on 2011-02-07
Hi Guys, how to know if i'm working with IPv4 or IPv6 ?, is possible to work with both ?, and how to enable or disable ipv4 or ipv6 ????, my linux is ubuntu 10.04

Tkx

---

### Post by ikt on 2011-02-07
Most likely ipv4, most of the world has yet to adopt ipv6.

---

### Post by expatCM on 2011-02-07
I wonder if there is any reason why you should NOT have IPv6 enabled.  It has to be deployed sooner rather than later.  

There seems to be a 24 hour trial on June 8
[http://www.networkworld.com/news/2011/012411-cisco-verizon-ipv6-trial.html](http://www.networkworld.com/news/2011/012411-cisco-verizon-ipv6-trial.html)

---

### Post by Willye on 2011-02-07
> **expatCM said:**
> I wonder if there is any reason why you should NOT have IPv6 enabled.  It has to be deployed sooner rather than later.  

There seems to be a 24 hour trial on June 8
[http://www.networkworld.com/news/2011/012411-cisco-verizon-ipv6-trial.html](http://www.networkworld.com/news/2011/012411-cisco-verizon-ipv6-trial.html)


```

```
It seems fine and good, but i want to know how to enable ip4 or ipv6 and how to check which is enabled .... 
```

```

---

### Post by zika on 2011-02-07
> **Willye said:**
> ```

```
It seems fine and good, but i want to know how to enable ip4 or ipv6 and how to check which is enabled .... 
```

```What does **ifconfig** gives You (in Terminal)?

---

### Post by wojox on 2011-02-07
There both enabled. Run 

```
ifconfig
```

It should show you an ipv6 address. If you want to use it you have to configure it with [Running IPv6 in practice]("http://www.debian-administration.org/article/Running_IPv6_in_practice").

---

### Post by Willye on 2011-02-07
> **wojox said:**
> There both enabled. Run 

```
ifconfig
```

It should show you an ipv6 address. If you want to use it you have to configure it with [Running IPv6 in practice]("http://www.debian-administration.org/article/Running_IPv6_in_practice").




```

```

ifconfig shows:

eth0      Link encap:Ethernet  HWaddr 00:0d:60:8b:c1:fe
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:0c:f1:a1:58:6f
          inet addr:9.172.222.91  Bcast:9.172.223.255  Mask:255.255.252.0
          inet6 addr: fe80::20c:f1ff:fea1:586f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:220846 errors:511 dropped:511 overruns:0 frame:0
          TX packets:8283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:39447245 (39.4 MB)  TX bytes:694407 (694.4 KB)
          Interrupt:11 Base address:0x2000 Memory:c0210000-c0210fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```

```

---

### Post by careertargetph on 2011-02-07
But of the machines right now is using IP4 may be in the future we will convert into IP6.

---

### Post by Willye on 2011-02-07
> **careertargetph said:**
> But of the machines right now is using IP4 may be in the future we will convert into IP6.

```

```
there is a procedure to configure IPV6, if i configure ipv6, after that,  HOW HELL does somebody knows if is installed IPV4 or IPV6 ???

is there command or file where i could see it?????

it's as simple like that    :mad:
```

```

---

### Post by uRock on 2011-02-07
If you have a router, then most likely your internal LAN will always be IPv4 unless you decide to make you internal network IPv6, which would be pointless.

Ubuntu can handle both.

---

### Post by philinux on 2011-02-07
> **Willye said:**
> Hi Guys, how to know if i'm working with IPv4 or IPv6 ?, is possible to work with both ?, and how to enable or disable ipv4 or ipv6 ????, my linux is ubuntu 10.04

Tkx

If you right click on the newtwork manager icon and choose edit connections you can enable ipv6. By default it is set to ignore,

snip

---

### Post by walt.smith1960 on 2011-02-07
How about this?  Ubuntu 10.10 desktop default, wireless connection.  System -> preferences -> Network Connections. Click the wireless tab, select the network connection in use then click 'edit'.  Enter your administrative password. There should be wireless, IP4, IP6 and wireless security tabs.  Click the IP6 tab, mine says 'ignore'.  When I select any other choice, my network connection disconnects.

Edit:  I needed to to set IP6 to automatic, IP4 to ignore. Now it seems to work.  I'm not sure how to check on which the ISP is using.

Edit 2:  Disabling IP4 and setting IP6 to automatic worked--until I did a suspend/resume cycle.  Both dots in network manager were green but would not connect.  When I set IP6 to ignore and set IP4 to auto I was back in business.  For all the talk about IP4 running out of addresses and needing IP6, it looks like there's a ways to go.

---

### Post by philinux on 2011-02-07
> **walt.smith1960 said:**
> How about this?  Ubuntu 10.10 desktop default, wireless connection.  System -> preferences -> Network Connections. Click the wireless tab, select the network connection in use then click 'edit'.  Enter your administrative password. There should be wireless, IP4, IP6 and wireless security tabs.  Click the IP6 tab, mine says 'ignore'.  When I select any other choice, my network connection disconnects.

Edit:  I needed to to set IP6 to automatic, IP4 to ignore. Now it seems to work.  I'm not sure how to check on which the ISP is using.

Arrgghh, Logged out then in and it is indeed borked if ipv6 is enabled. :confused:

---

### Post by The Cog on 2011-02-07
Look at this output from ifconfig that you posted:
> lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
The loopback port has both an IPv4 (inet) address and an IPv6 (inet6) address. So both protocols are present on your computer.
127.0.0.1 is the IP4 loopback address, 
and ::1 is the IPv6 loopback address.

---

### Post by Willye on 2011-02-08
> **uRock said:**
> If you have a router, then most likely your internal LAN will always be IPv4 unless you decide to make you internal network IPv6, which would be pointless.

Ubuntu can handle both.

```

```
ok, i understand that ipv4 is the standard and i could configure ipv6 etc etc etc, my final question is:

is there a command or file  where i can see if ipv4 or ipv6 is configured and enabled ?????
```

```

---

### Post by Lucradia on 2011-02-08
> **ikt said:**
> Most likely ipv4, most of the world has yet to adopt ipv6.

Your ISP also needs to support IPv6. Mine does not.

---

### Post by expatCM on 2011-02-08
hmmm ...  my reply just got lost ....  more or less what I wrote was ...

Sorry, I do not understand.  It is written above that 

> .....make you internal network IPv6, which would be pointless.

Why would it be pointless?  Having an IPv6 lan would support what is coming.  The WAN may be IPv4 but that will change and soon.  When it does it will be simply using a different DNS server to make the change.  So why not do it now for the internal traffic, at least you would know that it worked ... ?

---

### Post by ikt on 2011-02-08
> **expatCM said:**
> Why would it be pointless?

Because there's no shortage of IP addresses on your internal network.


> **Willye said:**
> ```

```
is there a command or file  where i can see if ipv4 or ipv6 is configured and enabled ?????
```

```

Yeah right here:

[http://www1.ubuntuforums.org/showpost.php?p=10436090&postcount=6](http://www1.ubuntuforums.org/showpost.php?p=10436090&postcount=6)

I think the question at this point is less about where you can see if ipv4 or ipv6 is configured and enabled and more about **why** you want to know if ipv4 or ipv6 is configured and enabled.

---

### Post by freak42 on 2011-02-08
Hello

I didn't follow the whole conversation, however for everyone interested in this topic:

A quick and easy way to see whether you have ipv6 network capabilities is to try to access a ipv6 only website such as:
[http://ipv6.google.com/](http://ipv6.google.com/)

If you get a connection error you don't have ipv6 or it is configured incorrectly.

hth
m.

---

### Post by uRock on 2011-02-08
> **ikt said:**
> Because there's no shortage of IP addresses on your internal network.
I think the question at this point is less about where you can see if ipv4 or ipv6 is configured and enabled and more about **why** you want to know if ipv4 or ipv6 is configured and enabled.
Agreed. The typical LAN doesn't need IPv6, though there isn't anything wrong with people setting it up. (It is a good chance to get some practice for us networking people.)

I really do not think people have much to worry about with configuring IPv6 when it comes to their neighborhood, unless they don't have a router at home and they are using prehistoric OSes.

---

### Post by Lucradia on 2011-02-08
> **freak42 said:**
> If you get a connection error you don't have ipv6 or it is configured incorrectly.

My IPv6 is configured to receive configuration automatically (via DHCP IPv6.) But since my ISP doesn't support it, I can't use it.

---

### Post by herdwick on 2011-02-08
inet addr:9.172.222.91 Bcast:9.172.223.255 Mask:255.255.252.0
inet6 addr: fe80::20c:f1ff:fea1:586f/64 Scope:Link

it has both, top is IPv4, bottom obviously is IPv6

---

### Post by lemming465 on 2011-02-08
If you want to know what your IPv6 status is, one site I like is [test-ipv6]("http://test-ipv6.com").  It will tell you your IPv4 and IPv6 addresses, and figure out how well DNS name translations and HTTP web connections are likely to work for you.  With links to explanations of what will probably happen with v4-only, dual-stack (v4+v6) and v6-only sites.  Currently most sites are v4-only, a few dual-stack, and pretty much none v6-only.  That will change over time.

People who need to be working hard on IPv6 are (1) ISP's and hosting providers, because businesses are going to demand it.  (2) Some businesses, particularly if they have asian customers, asian supply chains, mobile customers, or government contracts.  Or if they want to steal future business from v4-only luddites; having IPv6 access externally is about to become a competitive advantage.

Consumers can sit on their hands for 12-18 months, waiting for the supply of IP-v6 capable dual-stackable broadband modems (Cable, DSL) and WIFI routers to improve.  Converting to v6 is a lot like the analog to digital TV conversion; it takes years, many players have to do stuff, we all have to buy newer network gear, and we end up with mostly the same content when it's done.  In 2011 and probably 2012 there won't be much IPv6-only content to access, so there is no rush.

Enthusiasts don't have to wait for their ISP to offer IPv6; they can set up "Ipv6 transition tunnels over IPv4" using a number of possible technologies such as 6in4 point to point, 6to4 anycast, or Teredo.  I recommend 6in4 tunnels with a tunnel broker such as hurricane electric, sixxs, or gogo6.  6to4 requires a public IP address and has about a 15% failure rate, and Teredo is only for masochists.  On Ubuntu, the tunnelbroker.net tunnels from Hurricane Electric require a hand-configuration step where you cut & paste some "ip" commands into a terminal window.  sixxs and gogo6 can be run automatically by installing and configuring the "gogoc" client, once you have set up a tunnel account with them.  For 6to4, I like a [new zealand tun6to4 script]("http://www.anyweb.co.nz/tutorial/Linux6to4Host").  For Teredo, you need to install the "miredo" package and make sure /etc/default/miredo has *START_MIREDO=true* in it.  You do need a broadband modem and or wifi router that pass IP protocol 41 (IP in IP tunneling).

---

### Post by lemming465 on 2011-02-08
Beware!  IPv6 addresses starting with FE80:://64 are link-local, the v6 equivalent of 169.254.0.0/16 v4 zeroconf addresses.  You can't get anywhere global with them.

"Real" IPv6 addresses start with "2".  If all you see a a single FE80 thing, you probably have a live v6 stack on your host (normal) with no offsite v6 connectivity to the global v6 internet (depressing).

---

