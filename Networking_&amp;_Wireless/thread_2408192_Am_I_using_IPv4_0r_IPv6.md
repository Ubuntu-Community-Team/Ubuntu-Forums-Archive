---
title: "Am I using IPv4 0r IPv6?"
date: 2018-12-15
forum: Networking &amp; Wireless
---

### Post by echotech2 on 2018-12-15
No problems, just curious and know enough to be dangerous. 

  I was wondering if there is a way to determine if I am using IPv4 or IPv6 DNS (e.g. when using FireFox) .  FWIW I'm using cloudfares' DNS (1.1.1.1, 1.0.0.1  &  2606:4700:4700::1111, 2606:4700:4700::1001)

---

### Post by The Cog on 2018-12-15
Well, if you go to an IPv4-only website then you are using IPv4.
If you go to an IPV6 website, you are using IPv6. 
If you go to a website that implements both IPv4 and IPv6, then you are probably using IPv6.

ubuntuforums.org is an IPv4 only dinosaur.
[www.google.com](www.google.com) is both IPv4 and IPv6
loopsofzen.co.uk is apparently IPv6 only but because I have a dinosaur ISP (Virgin) I can't reach that site to see what it actually is.

The command **ss -nt** lists all current (and recent) TCP connections and you will be able to see from the addresses which connections are IPv6.

P.S. the command **host** followed by a name will list all its addresses so you can see which sites are which protocol. e.g.
```
steve@StevesPC:~$ host [www.google.com](www.google.com)
[www.google.com](www.google.com) has address 172.217.23.4
[www.google.com](www.google.com) has IPv6 address 2a00:1450:4009:801::2004
```

---

### Post by echotech2 on 2018-12-15
Thanks for the info.

  Also: 
```
dave@scamper:~$ ss -nt
State   Recv-Q    Send-Q        Local Address:Port         Peer Address:Port    
dave@scamper:~$
```



  Although my ISP, cogeco,  supposedly supports IPv6 at loopsofzen.co.uk just get the "unable To Connect" page.

---

### Post by The Cog on 2018-12-16
**ss -nt** will only show current or very recent connections.

**ip -6 ro** will show your IPv6 routing table, which should indicate whether your ISP is providing you with an IPv6 default route.

---

### Post by echotech2 on 2018-12-17
FYI The Cog  No idea what it means but:

```
dave@scamper:~$ ip -6 ro
fe80::/64 dev enp4s0 proto kernel metric 100 pref medium
fe80::/64 dev enp4s0 proto kernel metric 256 pref medium 
```

Also did this again:

```
dave@scamper:~$ ss -nt
State   Recv-Q    Send-Q        Local Address:Port         Peer Address:Port    
ESTAB   0         0              x.x.x.x                           208.92.52.36:80      
ESTAB   0         0             x.x.x.x                            208.92.52.36:80 
```

---

### Post by The Cog on 2018-12-17
Your only IPv6 routes are local - no default route for IPv6 so you have no IPv6 connectivity out through your ISP. **ip -4 ro** will show you what an IPv4 default route looks like.

ss -nt shows you have two established connections at the time you issued that command. 

You have posted your own public IPv4 address there (starting 67). You may want to edit your last post and redact that. Some folk get nervous about publishing their own IP address.

---

### Post by echotech2 on 2018-12-18
I see the info from ip -4 ro but I should get something similar for ip -6 ro? don't understand if this is an ISP thing or.....?

  FWIW, my wired and only internet connection shows:
  
IPv4 Method is "Automatic (DHCP) - DNS is 1.1.1.1, 1.0.0.1, "Automatic Off" - Routes is "Automatic On", The fields are blank.
IPv6 Method is "Automatic" - DNS is  2606:4700:4700::1111, 2606:4700:4700::1001, Automatic is off - Routes is "Automatic On" Fields are blank.

---

### Post by The Cog on 2018-12-18
Sorry, I don't know that one. I haven't yet had the pleasure of being connected to an ISP that actually provides IPv6 connectivity. 
Looking at the list of options, I would guess Automatic should be the one, so I guess your ISP is not providing IPv6. But maybe someone with IPv6 could confirm?

---

### Post by mitesh.agrwl on 2018-12-18
> **echotech2 said:**
> I see the info from ip -4 ro but I should get something similar for ip -6 ro? don't understand if this is an ISP thing or.....?

  FWIW, my wired and only internet connection shows:
  
IPv4 Method is "Automatic (DHCP) - DNS is 1.1.1.1, 1.0.0.1, "Automatic Off" - Routes is "Automatic On", The fields are blank.
IPv6 Method is "Automatic" - DNS is  2606:4700:4700::1111, 2606:4700:4700::1001, Automatic is off - Routes is "Automatic On" Fields are blank.

If the ISP connectivity is directly connected to your computer (not though a router), it is masking the details, but configuring routes for your machine.

```
$route -eF
``` will show a the routes configured by ISP. IPv6 DNS address indicates that there is possibility to connect IPv6 only websites, a call to ISP technical support might be helpful.

---

### Post by echotech2 on 2018-12-19
@mitesh.agrwl  Direct connection, no router.

```
dave@scamper:~$ route -eF
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         d67-193-68-1.ho 0.0.0.0         UG        0 0          0 enp4s0
xx.xxx.xx.x     0.0.0.0         255.255.252.0   U         0 0          0 enp4s0
link-local      0.0.0.0         255.255.0.0     U         0 0          0 enp4s0 
```

  My ISP (cogeco.ca) is one of those "We only support Windows" ones, and from what I've read doesn't care much about Windows either unless you want to buy something.  I was forwarded to so-called "Tech Support" and he asked me to click on some obviously Windows programs. Informed that I'm not using Windows, I got the "We only support......." spiel and offered no more help.

---

### Post by mitesh.agrwl on 2018-12-19
> ```
dave@scamper:~$ route -eF
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         d67-193-68-1.ho 0.0.0.0         UG        0 0          0 enp4s0
xx.xxx.xx.x     0.0.0.0         255.255.252.0   U         0 0          0 enp4s0
link-local      0.0.0.0         255.255.0.0     U         0 0          0 enp4s0
```

As confirmed already it is IPv4 only.

```
IPv4 Method is "Automatic (DHCP) - DNS is 1.1.1.1, 1.0.0.1, "Automatic Off" - Routes is "Automatic On", The fields are blank.
IPv6 Method is "Automatic" - DNS is  2606:4700:4700::1111,  2606:4700:4700::1001, Automatic is off - Routes is "Automatic On" Fields  are blank.
```
[URL="https://www.cloudflare.com/learning/dns/what-is-1.1.1.1/"]
Answer[/URL].

---

