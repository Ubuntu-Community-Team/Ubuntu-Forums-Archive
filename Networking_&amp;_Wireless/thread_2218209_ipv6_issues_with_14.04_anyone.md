---
title: "ipv6 issues with 14.04 anyone?"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by fr33z0n3r on 2014-04-19
I just upgraded from 13.10 today.  Has anyone seen issues with ipv6?  My router provides ip addresses for me for a Hurricane Electric tunnel I've had for a long time.  I appear to be getting addresses, but the host does not appear to be doing ipv6 as I would expect.  Ex, Facebook used to have an ipv6 entry, and I cannot get one to appear via DNS.  (I admittedly am now having a dns issue with ipv6 per the site below)

Using the test ipv6 site, shows that ipv6 works.  

[http://test-ipv6.com/](http://test-ipv6.com/)


My Connection properties do not display ipv6 info, but if I do an ifconfig, I see global unicast ipv6 addresses on the eth0 interface.

So my guess is that something is up with ipv6.  But I could be wrong.  Maybe I've never done testing with ipv6 on my Ubuntu install before.  With Windows 7, it would prioritize the ipv6 stuff leading to lots of indicators, and dns results that could validate it was enabled.

---

### Post by kossut on 2014-08-11
after upgrading from 12.04 both 13.10, 14.04 I have issue with:
- unable to add manually Ipv6 dns addresses
- no dns ipv6 autoconfiguration from dhcpv6 or RA offer..

---

### Post by jbdough on 2015-03-12
I think they have address and gateway transposed here
[https://wiki.ubuntu.com/IPv6#Get_connected_with_Hurricane_Electric](https://wiki.ubuntu.com/IPv6#Get_connected_with_Hurricane_Electric)
> [COLOR=#333333][FONT=Ubuntu Beta]For the address put the first address in your Routed 64. (In this example it would be **2001:470:a:d29f::1** .) For the prefix put in 64. For the gateway, put in the address from the "Client IPv6 address" of the tunnel details page (in this example it would be **2001:470:a:d29f::2**). Click apply.[/FONT][/COLOR]
That part of the instructions looks exactly backwards to me.

update: behind the Comcast gateway.  Ethernet connected directly to the gateway I don't even need 6to4 on my 32 bit ThinkPad
Ubuntu 14.04.2 LTS 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:08:14 UTC 2015 i686 i686 i686 GNU/Linux

follow-up:
When I got the tunnel to work the first time I was using DHCP all the way through:

from the Comcast gateway -> [ethernet/DHCP] -> internal NAT router -> [wifi/DHCP] -> to desktop

The native IPv6 offered by Comcast is apparently only dished up to ethernet-connected devices and I'm pretty sure DHCP only. 
[http://www.comcast6.net/index.php/ipv6-deployment-faq](http://www.comcast6.net/index.php/ipv6-deployment-faq)

Changing the  internal NAT router -> [wifi/DHCP] to static IP broke the tunnel.
Changing it back to DHCP:
> 
Your IPv4 address on the public Internet appears to be xx.xxx.xxx.xx
(COMCAST-33490 - Comcast Cable Communications, Inc.,US)

Your IPv6 address on the public Internet appears to be xxxx:xxx:x:xxx::x
(HURRICANE - Hurricane Electric, Inc.,US)

It appears that you use a tunnel mechanism for either IPv4 or IPv6.

Your DNS server (possibly run by your ISP) appears to have IPv6 Internet access.

Ubuntu 14.04.2 LTS 3.13.0-46-generic #77-Ubuntu SMP Mon Mar 2 18:23:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

