---
title: "[SOLVED] How to find out IPv6 addresses of websites?"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by sci-fi guy on 2008-03-07
Just as the title says: how can I find out what the IPv6 address of a website is (assuming it has one)? I usually use ping for finding out the IPv4 address, but what do I use for v6?. I have seen some mentions of a ping6 command on the 'net, but the instructions aren't yielding anything.

---

### Post by Paris Heng on 2008-03-07
> **sci-fi guy said:**
> Just as the title says: how can I find out what the IPv6 address of a website is (assuming it has one)? I usually use ping for finding out the IPv4 address, but what do I use for v6?. I have seen some mentions of a ping6 command on the 'net, but the instructions aren't yielding anything.

Dear,

To check IPv6 of particular website, you can try using the command **nslookup**, example my university website, I not sure this is the right way, I have found particular website with its ipv6 address, but forget how-to, hope this can give you a bit of idea.

> heng@heng:~$ nslookup
> set q=any
> [www.mmu.edu.my](www.mmu.edu.my)
Server:         202.188.0.133
Address:        202.188.0.133#53

Non-authoritative answer:
[www.mmu.edu.my](www.mmu.edu.my)  canonical name = [www.cyber.mmu.edu.my](www.cyber.mmu.edu.my).

Authoritative answers can be found from:
mmu.edu.my      nameserver = ns3.mmu.edu.my.
mmu.edu.my      nameserver = mmu.edu.my.
mmu.edu.my      nameserver = ns4.mmu.edu.my.
ns4.mmu.edu.my  internet address = 219.94.43.146
mmu.edu.my      internet address = 203.106.62.11
ns3.mmu.edu.my  internet address = 203.106.62.61
ns3.mmu.edu.my  has AAAA address **2001:e68:2000:6403:203:baff:fe04:f040**


Refer to: [http://oversteer.bl.echidna.id.au/IPv6/sun/files/c0204.htm]("http://oversteer.bl.echidna.id.au/IPv6/sun/files/c0204.htm")

--------------------------------------
[Paris Heng @ Wifi-Linux]("http://parisheng.110mb.com/")

---

