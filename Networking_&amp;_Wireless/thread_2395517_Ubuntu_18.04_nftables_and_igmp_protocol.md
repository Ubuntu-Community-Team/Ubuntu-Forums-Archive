---
title: "Ubuntu 18.04 nftables and igmp protocol"
date: 2018-07-03
forum: Networking &amp; Wireless
---

### Post by lensman3 on 2018-07-03
Which application is hitting my network with protocol igmp.  The nftable command is

[HTML]ip protocol igmp counter drop[/HTML]

and reports the firewall using "nft list ruleset -nn"

[HTML]ip protocol igmp counter packets 6 bytes 192 drop[/HTML]

As you can see the computer that this is on has been running a while since 6 packets have been dropped with a total byte length of 192.

I run nft as both the IPV4 and IPV6 firewall together and this line is on the input side of the firewall.  
My dns server is a dnsmasq and it provides IPV6 address for 2^64  addresses which have a life of about 15 minutes and I get another IPV6 address.
I run arno;s firewall on my linux firewall with both IPV4 and IPV6 running.  Generally, the IPV6  firewall is not as strong as the IPV4 firewall. 
My provider is CenturyLink fiber (south Denver area).

I suspect these packets are from CenturyLink and are sniffing my network. Igmp is protocol 2 in /etc/protocols.  

I just added the same command to the output side of my nft firewall.  

My CenturyLink firewall/modem is set in pass through mode has been for a year.

Anybody know what is going on?

---

