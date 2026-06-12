---
title: "Configuring WideDHCP Client to automatically calculate sla_len"
date: 2016-05-16
forum: Networking &amp; Wireless
---

### Post by Sajal_Malhotra on 2016-05-16
[COLOR=#333333][FONT=Helvetica]I am using Wide DHCPv6 Client on my Machine. What i am trying to achieve is rather simple: 
1. I want dhcpv6 client to get Prefixes from my network using Prefix Delegation. 
2. Once the client gets the prefix, i want it to assign 64 bit Network Prefix to the different ethernet interfaces.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]While reading the following manual page on Wide DHCPv6 Client configuration:
[http://manpages.ubuntu.com/manpages/wily/man5/dhcp6c.conf.5.html](http://manpages.ubuntu.com/manpages/wily/man5/dhcp6c.conf.5.html)[URL="https://wiki.openwrt.org/doc/uci/dhcp6c"]
https://wiki.openwrt.org/doc/uci/dhcp6c[/URL]

What i understood is that "sla_len" in section below "Specifies the site level aggregator length which is the difference of 64 and the delegated prefix size", e.g. /64 minus /56 from ISP = 8:[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]config 'interface' 'lan'
        option 'enabled' '1'
        option 'sla_id'  '0'
        option 'sla_len' '8'[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]Now the problem is that if i don't know the "delegated prefix size" assigned by Network before hand, how can i hard-code the value of "sla_len"?
Is there a way to force client to automatically take the value of this parameter based on the delegated prefix size allocated by Server. For e.g. if DHCP server assigns /61 bit Prefix then this parameter automatically takes the value as 3 (64-61)? 
Or alternatively is there a way to detect the delegated prefix length allocated by server before hand and then configure the Client accordingly?[/FONT][/COLOR]

---

