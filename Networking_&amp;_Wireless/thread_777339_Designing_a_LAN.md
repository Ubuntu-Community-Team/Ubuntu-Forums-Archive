---
title: "Designing a LAN"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by MrQuincle on 2008-05-01
Dear all,

So many posts here, I guess it will solve a lot of questions, if some fundamental issues are tackled that underlie all those. Perhaps the LAN I want to have in my student house will be a good case for that. :popcorn:

Our internet provider (ISP) gave us a CopperJet 1616, with only one connection. So there is a hub with 8 cables right behind it. In this student house there are at least 6 computers, so that is needed. From the ISP we got a WAN IP, something like 82.XXX.XXX.XXX that is mapped to an IP address on our LAN, namely 172.19.3.1. The "default gateway" parameter on this modem is set to 0.0.0.0.

**Wireless Router**
Now, we need to have wireless internet too. So, I bought an Edimax EW-7209APg. I placed this wireless router behind the hub. This by just pulling out the connector from my desktop, connecting it through this wireless router instead. I want exactly this setup, because:
[LIST]
[*]I can remove the Edimax easily when I move to another house
[*]I can leave the Copperjet in place
[*]I can use the wired connectors on the Edimax for my other computers
[/LIST] 
The wireless router got a static IP address in the same way as my desktop computer, see next section. Namely at 172.19.3.200.

**Static IP address**
On my standard desktop I have an Apache web server, and I want to be able to use it from outside. So, I need a static IP address for it. For that reason I entered some information on the Copperjet. To "Existing DHCP fixed IP/MAC mappings" my desktops IP address at 172.19.3.100 together with its MAC address. And I added also a "reserved mapping" to the NAT configuration on the Copperjet mapped to the port where my Apache server is listening, say 1234. With a dynamic DNS service I am now able to reach my computer from outside. And that works, if I test it, I have to do it via a proxy. That seems to be called "local loopback", but from the viewpoint of the router!

So, now the big questions arise. :guitar: How do I configure all this? When I just try I get things working, but only for a few minutes or so. Some of the problems I encounter: 
[LIST=1]
[*]The Copperjet runs out of memory after a while. Wow!
[*]Lots of computers don't have internet when there leases run out. 
[*]DNS doesn't seem to be working. 
[*]One of my Ubuntu machines can see another (both without firewill), but not the other way around.
[/LIST]

**DNS**
So, I was fooling around in ```
/etc/resolv.conf
``` but that becomes overwritten each time, so I changed to ```
/etc/dhcp3/dhclient.conf
``` where I added for example:
```

prepend domain-name-servers 172.19.3.1;
prepend domain-name-servers 212.29.160.1;
prepend domain-name-servers 212.29.161.254;

```
The first is my router. The second just a common DNS server. But actually I have no clue about what I am doing! I have the two above mentioned 212.29.X.X DNS servers listed on the Copperjet. So, what I need to know is why this is not enough! What does someone need to do normally? On my wireless I can refer to the DNS server as the 172.19.3.1 and that will do? And on my computers that are connected to the wireless Edimax, do I need to refer to the DNS server as 172.19.3.1 or as 172.19.3.200 (the IP address of the latter).

**DHCP**
The next big thing I don't get my head around is what to do with DHCP. On my LAN, I have 172.19.X.X as "DHCP server subnet" on my Copperjet. I tried, but can't change it to 172.19.3.X, so everywhere I tried to change netmasks on my computers from the default 255.255.255.0 to 255.255.0.0 where appropriate. Don't know if that's important, or that the broadcast messages can be picked up anyway...

If I don't run a DHCP server on the wireless Edimax, I don't get an IP address. So, apparently the Edimax is not able to relay the request for an IP to the Copperjet, am I right in that? So, when I run a DHCP server on the Edimax, can I just give away the addresses from 172.19.3.2 to 172.19.3.99? And which DHCP addresses do I need to give away on the Copperjet? Also from 172.19.3.2 to 172.19.3.99, or does that conflict? And do I actually need to release 172.19.3.101 till 172.19.3.199? Or wont it get past the Copperjet in that case?

Thanks a lot in advance! Hope I am not too much of an annoyance. If you need any information, I will be glad to provide it.

---

