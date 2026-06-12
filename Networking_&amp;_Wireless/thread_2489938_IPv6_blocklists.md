---
title: "IPv6 blocklists"
date: 2023-08-15
forum: Networking &amp; Wireless
---

### Post by actionmystique2 on 2023-08-15
Some sites such as [Cisco Talos]("https://www.talosintelligence.com/resources/ip-blacklist"), [Abuse]("https://sslbl.abuse.ch/blacklist/sslipblacklist.txt") and the aggregator [FireHOL]("https://github.com/firehol/blocklist-ipsets") provide the community with some lists of rogue and malicious IPv4 addresses and subnets.

Could anyone share some similar URLs regarding IPv6 ranges?

I'm aware of the gigantic space allocated to the public IPv6 adressses, but these blocklists could still help everyone strength the security of all dual-stacked (or IPv6-only) public websites and private networks.

---

### Post by TheFu on 2023-08-15
My ISP gives me a /54, if I ask.  

```
IPv6 Subnet Calculator for /54
Result

IP Address:	2001:db8:85a3::8a2e:370:7334/54
Full IP Address:	2001:0db8:85a3:0000:0000:8a2e:0370:7334
Total IP Addresses:	**18,889,465,931,478,580,854,784**
Total /64 Networks:	1,024
Network:	2001:0db8:85a3:0000::
IP Range:	2001:0db8:85a3:0000:0000:0000:0000:0000 - 2001:0db8:85a3:03ff:ffff:ffff:ffff:ffff
```

That's just for 1 house.  [https://xkcd.com/865](https://xkcd.com/865)
IPv6 is setup so that every new connection can add a new IP.  Basically, each unique visitor can come from a different IP AND that capability is built-into IPv6 standards.  It becomes like hiding a single needle in a haystack that covers Asia + Europe.

[https://www.spamhaus.org/organization/statement/012/spamhaus-ipv6-blocklists-strategy-statement](https://www.spamhaus.org/organization/statement/012/spamhaus-ipv6-blocklists-strategy-statement) is what SpamHaus says. They don't appear to support it today and they are professionals in blocklists. It is their core business.

---

### Post by actionmystique2 on 2023-09-11
The idea is to get a list of rogue IPv6 subnets, not /128 addresses of course.

---

