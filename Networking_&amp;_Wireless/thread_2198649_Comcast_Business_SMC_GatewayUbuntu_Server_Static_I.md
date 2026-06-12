---
title: "Comcast Business SMC Gateway/Ubuntu Server Static IP configuration"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by chris143 on 2014-01-09
I'm using ubuntu-server, and have a comcast business line with 5 static IPs(/29)

We'll say this IP range is 173.8.168.104/29,
The SMC Gateway/modem/router crap comcast installed as chosen the static IP 173.8.168.110 for it's self, and I've just installed a new ubuntu server machine into the network and would love to have it set to one of the static IPs provided by comcast.

However upon writing the following into my /etc/network/interfaces, I notice I have no connectivity what so ever.

```

address 173.8.168.104
netmask 255.255.255.248
network 173.8.168.104/29
broadcast 173.8.168.111
gateway 173.8.168.110

```

I haven't bothered with the actual DNS servers as at this point after setting such and attempting sudo /etc/init.d/networking restart, or attempting ifdown eth0/ifup eth0 or even a full reboot and attempting to ping say 8.8.8.8 I get the following output.


From 173.8.159.104 icmp_seq=1 Desitnation Host Unreachable.

So I'm assuming for some reason it's routing the connections wrong, or something else is going on I'm a Sys Admin and generally avoid the networking side of things if there's an easier solution but I figure this is a time to start to learn a bit more about what's going on here.

So have I done something wrong? is my first question.

I truly don't believe I did however, obviously it's not working so there's gotta be something monkeyed up somewhere....
I've been through several guides on the actual configuration of the SMC gateway it's self and all my settings are the same as what they give you there, so any help would be greatly appreciated.

---

### Post by bab1 on 2014-01-10
> **chris143 said:**
> I'm using ubuntu-server, and have a comcast business line with 5 static IPs(/29)

We'll say this IP range is 173.8.168.104/29,
The SMC Gateway/modem/router crap comcast installed as chosen the static IP 173.8.168.110 for it's self, and I've just installed a new ubuntu server machine into the network and would love to have it set to one of the static IPs provided by comcast.

However upon writing the following into my /etc/network/interfaces, I notice I have no connectivity what so ever.

```

address 173.8.168.104
netmask 255.255.255.248
network 173.8.168.104/29
broadcast 173.8.159.111
gateway 173.8.[COLOR="#FF0000"]159[/COLOR].110

```

I haven't bothered with the actual DNS servers as at this point after setting such and attempting sudo /etc/init.d/networking restart, or attempting ifdown eth0/ifup eth0 or even a full reboot and attempting to ping say 8.8.8.8 I get the following output.


From 173.8.[COLOR="#FF0000"]159[/COLOR].104 icmp_seq=1 Desitnation Host Unreachable.

So I'm assuming for some reason it's routing the connections wrong, or something else is going on I'm a Sys Admin and generally avoid the networking side of things if there's an easier solution but I figure this is a time to start to learn a bit more about what's going on here.

So have I done something wrong? is my first question.

For starters the network should be stated as ```
network 173.8.168.104
```...no need to add the /29 
Also you have misstated the broadcast address.  It should be ```
broadcast 173.8.168.111
```...the last number in the subnet range.
> 

I truly don't believe I did however, obviously it's not working so there's gotta be something monkeyed up somewhere....
I've been through several guides on the actual configuration of the SMC gateway it's self and all my settings are the same as what they give you there, so any help would be greatly appreciated.

I don't see why you have DHCP working at all.  It's not needed.  Comcast is providing you immutable (non-changing) IP addresses.  You decide whether you distribute them via DHCP (dynamically) or by configuring a flat file (statically).  Even if you use DHCP reservations to provide a non-changing IP address it is still dynamically served via a DHCP server.  Which do you prefer to use?  I have a larger network so I have DHCP running for 20 IP addresses and set my static addresses OUTSIDE of that 20 address range.

---

### Post by chris143 on 2014-01-10
The 8.XXX.104(in ICMP result) and 8.XXX.111(in broadcast) as well as 8.XXX.110(in gateway) was actually before I *masked* the IP with the range I was referring to before, so I just forgot to do those while I was writing the post and they actually are correct on the server configuration, if you could please edit that in your post I would appreciate it.

But I have indeed setup the broadcast to be the lats IP in that specific range and done so properly, 
It's my mistake to have not edited that properly in the post I was manually copying the configuration.

But I'm assuming there's something going on with the smart bridge crap in the SMC gateway if those are the only mistakes you saw, any other details or methods of testing/troubleshooting this would be greatly appreciated.

I do currently have DHCP disabled on the comcast SMC gateway.

I've also tried the configuration without the /29 on network and it produces the exact same results.


Now as for the DHCP, I've tried it with this both enabled and disabled and the Comcast SMC gateway came with it enabled and client workstations on the network do use it in order to receive internal addresses while we get approval on payment for additional networking hardware so this is a temporary thing and I don't plan to keep it that way.

---

