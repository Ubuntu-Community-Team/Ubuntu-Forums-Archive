---
title: "can using a switch interfere with net access?"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by whatrucrazy on 2007-01-22
just a quick question: 
a friend of mine is running dapper and has just moved into a new house where instead of using a router, they are using a switch to connect their 4 computers via a modem to the net. now whenever she tries to visit yahoo or google, the sites will not come up at all, even though almost all others do. when she reboots in XP though she has no problems, nor does anyone else in the house. I'v checked firefox and cookies..etc its all enabled.

now i'm wondering: is this to do with the fact that her ubuntu system is accesing the net via a switch rather than a router?

i'm asking so i can tell her whether she needs to buy a router (which i'd suggest anyway), or whether it's something i haven't though of.

thanks

---

### Post by koenn on 2007-01-22
> they are using a switch to connect their 4 computers via a modem to the net
Can you explain how they do that ? Do they have 4 separate accounts with their ISP , o an account that supports 4 computers ? Or something else ? 
Can 4 people/computers use the modem / access the internet simultanously ?

---

### Post by PilotJLR on 2007-01-22
Yeah, that's bad... they need a router. NAT functionality is required, and a switch can't provide that.
Machines work after reboots because they are sending another DHCP Offer, so they "steal" the public IP from whatever else took it.

So they need to go buy a router...

---

### Post by whatrucrazy on 2007-01-22
> **koenn said:**
> Can you explain how they do that ? Do they have 4 separate accounts with their ISP , o an account that supports 4 computers ? Or something else ? 
Can 4 people/computers use the modem / access the internet simultanously ?

it works like this:

an (1) account with their ISP (ADSL i think, can't remember checking)
a modem
a x4 switch plugged into the modem
4 computers then plugged into the switch

re: "stealing" via DHCP, i though the IP's were just assigned when requested, how is it stealing from someone else?

my question still remains though, is it the use of the switch that is causing the problems accessing some websites?

---

### Post by PilotJLR on 2007-01-22
No. You are confusing public with private addressing... you have 1 public IP address, so whichever machine has the most recent DHCPOFFER gets it, hence the stealing. I would imagine any machine with connectivity after the IP changes hands is working on only very small data exchanges, since you have duplicate IP addresses from the ISP's perspective.

Trust me, your setup is not going to work  :-)
buy a router.

Lookup NAT if you don't believe me
[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)

---

### Post by dmizer on 2007-01-23
could it be that the modem is also acting as a router?  because with only a switch and a modem, this would cause problems even in a windows environment unless there was SOME kind of network address translation involved (as shown in the wikipedia link posted by PilotJLR)

can you post the ip address off one of the windows machines?

---

### Post by RandomJoe on 2007-01-23
You do NOT necessarily need a router.  Most home DSL/cable connections give only one IP, in which case you would.  However, many also allow you to get multiple IPs if you pay for it.  In my case, I can get extra IPs for $10/mo each.  Not worth it, so I use the router, but it IS possible they are set up just fine with the switch.

It is also possible the DSL modem is doing the routing, although they usually have multiple ports on them if they do.  Does the modem have wireless on it?  If so, it definitely does.

If the computers are getting 192.168.x.x IP addresses, something is doing NAT for you.  (Every home NAT device I've seen gives that range, but there are a few others possible.)  Otherwise, you are probably getting public IPs from the ISP.  And the people suggesting a router are right, if every computer is getting the same IP.

Do you possibly need to send a specific machine name (perhaps an account name) with the DHCP request?  I remember seeing that as an optional field when setting up various Linux distros, it says some ISPs require it.  Perhaps Windows was set up to send the machine name and Linux was not?  I believe this would be done by adding the following line to /etc/dhcp3/dhclient.conf:
```
send host-hame "machinenamehere"
```

---

### Post by koenn on 2007-01-23
I'm with RandonJoe on this one. 

- If they have an ISP that allows multiple machines and gives out multiple public IP addresses, a switch is enough, and the cause of the network problems has to be looked for elsewhere 
the "send host-name" option is a good start

- if they're using 1 public IP address without routing and NAT, things should not work at all or might sometimes work and show very strange network behaviour and all sorts of trouble. 

- or we're missing something - like the modem is more than just a modem - a router/NAT device. 


It's quite easy to check this if you could just look which IP address **each** computer has while they are ***all*** (or at least more than 1) online.

---

