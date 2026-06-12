---
title: "How to set up a home Gateway Server using 2 Network Cards?"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by Josh1 on 2007-09-04
Here's what I want to have (Basically):

Modem ->
	         -> Router (Which assigns the Gateway Machine NIC1 the IP of 192.168.0.118)
		                 -> Ubuntu "Gateway" Machine (Network Card 1) [IP: 192.168.0.118]
		                      -> Network Card 2 [IP: 192.168.1.1]
                                           -> PC1 [IP: 192.168.1.2], PC2 [192.168.1.2], etc.

I have read alot of tutorials, even tried eBox set CD on a spare HDD (It installed a custom Debian Sarge 3.1 or something, but it couldn't get DHCP working properly but I could access it and it could see both NIC's).

What would be the best way of doing this? I want to have:

1) Modem connects from the wall to the..
2) Router, which gets my external IP from the modem, then has 1 cord going to my Ubuntu Gateway (NIC 1)
3) Network Card 1 gets the IP 192.168.0.118 from the router
4) Network Card 2 is assigned 192.168.1.1 by the Gateway
5) The other PC's connect to the gateway using a Static IP  Address (192.168.1.2 etc) which can then use the Gateway as a proxy server etc.

What I want to use the Gateway for:
- Static IP to the other PC's.
- SQUID Proxy
- Fileserver
- ETC ETC

Any ideas on how I would set this up?

Cheers,

Josh1

---

### Post by KCPokes on 2007-09-04
Would be easy enough to set up yourself, starting with a server install rather then a desktop.  As the machine itself will essentially always be open to external traffic, you want to reduce the number of possible security exploits.  Given that your current router handles the security, it is really just a matter of setting your routing rules on your gateway and installing your basic services.  

You may also want to look into IPCop or Smoothwall as prebuilt alternatives.  The would give you more then what you are requesting along with replacing your router.  Essentially your "firewall" hooks directly to your modem and separates your "green" network (internal) from your "red" network (external).  Out of the box it provides Squid, Full Firewall Control, Snort, etc..., thus worth a look.  Building yourself is far more entertaining, as well as a challenge, so I'd hate to talk you out of it, but it could also turn into a frustrating undertaking.

---

### Post by Josh1 on 2007-09-04
> **KCPokes said:**
> Would be easy enough to set up yourself, starting with a server install rather then a desktop.  As the machine itself will essentially always be open to external traffic, you want to reduce the number of possible security exploits.  Given that your current router handles the security, it is really just a matter of setting your routing rules on your gateway and installing your basic services.  

You may also want to look into IPCop or Smoothwall as prebuilt alternatives.  The would give you more then what you are requesting along with replacing your router.  Essentially your "firewall" hooks directly to your modem and separates your "green" network (internal) from your "red" network (external).  Out of the box it provides Squid, Full Firewall Control, Snort, etc..., thus worth a look.  Building yourself is far more entertaining, as well as a challenge, so I'd hate to talk you out of it, but it could also turn into a frustrating undertaking.

Thanks alot for the feedback! I'll take a look at the sites you provided. I love doing things myself. :)

Reason why I don't want to remove the Router is because of the Wireless access it provides to 2 laptops in the house, so it's not really an option to remove the router at this stage (though I have heard about putting in a wireless card or something and then the linux server acts as a wireless router.. then I wouldn't need  arouter at all).

Thanks for the time,
Josh

---

### Post by guardsman85 on 2007-09-04
> **KCPokes said:**
> Would be easy enough to set up yourself, starting with a server install rather then a desktop.

I'd agree.  It will be a lot better to start with a server installation.  After that it's just a matter of making sure we understand exactly what you're wanting to do (e.g. do you need to forward ports or do you just want a simple NAT box?  What all do you want to do with Squid? etc...)

Is there any reason you have to have any of your addresses assigned by DHCP?  I think doing both NIC's as static addresses would work just fine (if not better).

---

### Post by Josh1 on 2007-09-04
> **guardsman85 said:**
> I'd agree.  It will be a lot better to start with a server installation.  After that it's just a matter of making sure we understand exactly what you're wanting to do (e.g. do you need to forward ports or do you just want a simple NAT box?  What all do you want to do with Squid? etc...)

Is there any reason you have to have any of your addresses assigned by DHCP?  I think doing both NIC's as static addresses would work just fine (if not better).

No reason why the server is on DHCP.

Sure, I can just setup Ubuntu Server on my harddrive no problems at all.

I want to use SQUID to bring all traffic on my home network (except for the wireless traffic which will connect directly to the router using WiFi) so I can monitor all traffic etc.
I haven't really  looked into many proxies, but SQUID looks quite popular..

Cheers,
Josh

---

### Post by guardsman85 on 2007-09-04
> **Josh1 said:**
> I want to use SQUID to bring all traffic on my home network (except for the wireless traffic which will connect directly to the router using WiFi) so I can monitor all traffic etc.
I haven't really  looked into many proxies, but SQUID looks quite popular..


Yeah, I like SQUID.  However, depending on what you're wanting to monitor you could use Wireshark, TCP dump, or a similar program.  Basically, after your gateway machine is setup you could just setup one of those programs to monitor all traffic on eth1 (your WAN-side NIC).  Anyway, first things first...let us know when you've got the server installed and we get into the fun stuff!

---

### Post by KCPokes on 2007-09-04
> **Josh1 said:**
> Reason why I don't want to remove the Router is because of the Wireless access it provides to 2 laptops in the house, so it's not really an option to remove the router at this stage (though I have heard about putting in a wireless card or something and then the linux server acts as a wireless router.. then I wouldn't need  arouter at all).

Thanks for the time,
Josh

Actually you can keep the router but disable the DHCP aspect of it and allow the "gateway" to assign all DHCP requests.  That is the configuration I have set up at home, after fighting my Linksys router and its continued failure after VPN sessions.  I moved to a Smoothwall configuration a couple years ago and haven't looked back.  My old router sits there, having moved from 192.168.1.1 to 192.168.1.254, and merely acts as an access point, rather then a true router.

---

### Post by Josh1 on 2007-09-04
> **KCPokes said:**
> Actually you can keep the router but disable the DHCP aspect of it and allow the "gateway" to assign all DHCP requests.  That is the configuration I have set up at home, after fighting my Linksys router and its continued failure after VPN sessions.  I moved to a Smoothwall configuration a couple years ago and haven't looked back.  My old router sits there, having moved from 192.168.1.1 to 192.168.1.254, and merely acts as an access point, rather then a true router.

That sounds EXACTLY what I want to do. I'll take a look at smoothwall, it looks pretty sleek. :)

I would do this, right?:
Modem --> Router --> Ubuntu "Gateway" NIC1
Ubuntu "Gateway" NIC 2  --> Switch --> PC's

Cheers for the reply, really appreciated.
Josh

---

### Post by KCPokes on 2007-09-04
> **Josh1 said:**
> That sounds EXACTLY what I want to do. I'll take a look at smoothwall, it looks pretty sleek. :)

I would do this, right?:
Modem --> Router --> Ubuntu "Gateway" NIC1
Ubuntu "Gateway" NIC 2  --> Switch --> PC's

Cheers for the reply, really appreciated.
Josh

If you went the Smoothwall approach, you'd have:

Modem --> Ubuntu Gateway Nic 1 (Red)
Ubuntu Gateway Nic 2 (Green) --> Switch
Switch --> Router (DHCP disabled)
Switch --> PCs

You can have get even more elaborate, if you so desired, but bringing in an Orange (DMZ) and a Blue (Wireless) network.  The reason for the DMZ is pretty obvious, but people feel that the blue network, for wireless traffic is a good idea as well, given that you tend to open it to more people and it'll add a layer of segregation between your open "green" network and the wireless.  Personally that is overkill, but its definitely an option.

Just remember, if you go that route, that you'll need to disable DHCP and re-IP you current router, otherwise you'll run into conflicts.  

I've been down the road a couple different times so feel free to shoot me a message if you run into any issues.

Good luck.

---

### Post by guardsman85 on 2007-09-04
> **Josh1 said:**
> I would do this, right?:
Modem --> Router --> Ubuntu "Gateway" NIC1
Ubuntu "Gateway" NIC 2  --> Switch --> PC's
Ultimately your Ubuntu machine is just a second router, so if you wanted you could even do this (hope it makes sense!):

```
[Modem] o---o [eth1_Ubuntu_eth0] o---o [switch] o---o [PC_static_address]
                                            |
                                            |
    [PC_WIFI_DHCP_address] )))    ((( [Wireless Access Point]
```

EDIT:  Looks like KC beat me to the punch!  That way looks good too!

---

