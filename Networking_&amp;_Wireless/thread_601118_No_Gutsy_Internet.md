---
title: "No Gutsy Internet"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by Threbus5 on 2007-11-02
Hi,

I read multiple pages about Gutsy problems with establishing Internet connections. Most seem to suggest disabling Ipv6 in Firefox. Some suggest disabling Ipv6 in Ubuntu. Many discuss a DNS issue. Some describe an abilty to connect to everywhere else on a LAN but not to the Internet.

My experiences falls in between them. My machine uses a static IP. And, I tried DHCP with the same results  - so I do not appear to have an issue resolvable by using dynamic adressing.

After installing Gutsy, I can ping all local LAN addresses, including the router and Gateway. However, I cannot connect to the Internet.

In addition to the inability to connect to the Internet, I am unable to manually enter a DNS server address in the network manager. The inability to detect a DNS server may be the root of the problem. Which probably means that it would be a really good idea to configure the system with a DNS server.

However, the network manager does not accept, it does not even display any numbers as I try to type/add a DNS server (I tried from the number key pad and from the numbers across the keyboard top).

So, Please, how may a DNS server address be entered from the terminal?  (I read several posts that seem related to that issue but they assumed more knowledge than I seem to possess.)

Thank you very much.

---

### Post by dantrevino on 2007-11-03
Try "dig yahoo.com" from to see if you get a DNS response.  To manually set your dns:

sudo vim /etc/resolv.conf

It should have a format like:
```
search mydomain.com

nameserver 111.222.333.444
nameserver 111.222.333.445

```dan

---

### Post by Threbus5 on 2007-11-03
Hi and Thanks very much,

I really became suspicious of DNS when I was able to reach web sites using their IP addresses but not by name.

The resolv.conf file consisted of ONLY the following:
domain WORKGROUP

after adding 
nameserver xxx.xxx.xxx.xxx 

where the address was my Gateway address the Internet snapped in!

Although the Internet works now, I still cannot use the network manager to add DNS servers. That sounds as if it needs a bug report.

---

