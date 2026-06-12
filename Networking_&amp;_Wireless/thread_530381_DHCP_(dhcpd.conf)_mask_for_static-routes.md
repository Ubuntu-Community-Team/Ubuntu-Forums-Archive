---
title: "DHCP (dhcpd.conf) mask for static-routes"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by lcomunia on 2007-08-20
I could not figure out how to set the mask for a static route during the lease
I need to set up a route for the lan 10.35.151.0 through the GW 192.168.1.230 with the mask 255.255.255.0

My configuration shown below actually lease the route but using the mask 255.255.255.255 

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.1.150;
  option domain-name-servers 200.71.192.4, 200.71.192.5;
  option domain-name "vgl.cl";
  option routers 192.168.1.254;
  option static-routes 10.35.151.0 192.168.1.230;
  option broadcast-address 192.168.1.255;
}

Anyone knows how to correct that ??

Thanks in advance

Leonardo

---

### Post by Synflux on 2007-08-20
Hi,

I don't know if this is correct or if it works but I found an example on google:

option static-routes 10.0.1.0 131.243.1.86, 131.243.1.0 10.0.1.1;
	subnet 10.0.1.0 netmask 255.255.255.0 {
	}
	subnet 131.243.1.86 netmask 255.255.255.255 {
	}

Which seems to set the subnet mask after the static route statement?

I found this [Here]("http://www.cs.ucla.edu/classes/cs217/ns-allinone-2.1b4/ns-2/emulate/support/dhcpd.conf")

:confused:

---

### Post by lcomunia on 2007-08-20
Nope, don't work ...

The subnet tag stands for the leased group of IPs.
Then you have to set up your range and all the options like the static-route.

also I tried with the option subnet-mask with no positive results

I'm still looking and trying some combinations with no success.

Thanks

---

