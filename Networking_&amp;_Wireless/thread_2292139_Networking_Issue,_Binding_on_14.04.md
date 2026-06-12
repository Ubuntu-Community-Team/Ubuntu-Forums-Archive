---
title: "Networking Issue, Binding on 14.04"
date: 2015-08-25
forum: Networking &amp; Wireless
---

### Post by Bashed on 2015-08-25
IPs routed at the switch just fine.

```
interface Vlan100
 ip address xxx.xxx.235.1 255.255.255.0 secondary
 ip address xxx.xxx.236.1 255.255.255.0 secondary
 ip address xxx.xxx.237.1 255.255.255.0 secondary
 ip address xxx.xxx.238.1 255.255.255.0 secondary
 ip address xxx.xxx.56.1 255.255.255.0 secondary
 ip address xxx.xxx.57.1 255.255.255.0 secondary
 ip address xxx.xxx.58.1 255.255.255.0 secondary
 ip address xxx.xxx.59.1 255.255.255.0 secondary
 ip address xxx.xxx.100.1 255.255.255.0 secondary
 ip address xxx.xxx.101.1 255.255.255.0 secondary
 ip address xxx.xxx.102.1 255.255.255.0 secondary
 ip address xxx.xxx.103.1 255.255.255.0 secondary
 ip address xxx.xxx.192.1 255.255.255.0 secondary
 ip address xxx.xxx.193.1 255.255.255.0 secondary
 ip address xxx.xxx.194.1 255.255.255.0 secondary
 ip address xxx.xxx.195.1 255.255.255.0 secondary
 ip address xxx.xxx.37.89 255.255.255.248
```


**Interface config on the Ubuntu server**
[http://pasted.co/3d1f583b](http://pasted.co/3d1f583b)

**IFCONFIG OUTPUT**
[http://pasted.co/bc84690a](http://pasted.co/bc84690a)

[B]PROBLEM
[/B][http://pasted.co/56abbc08](http://pasted.co/56abbc08)

---

### Post by SeijiSensei on 2015-08-25
How about rather than pasting graphics you explain the problem in English?

---

### Post by Bashed on 2015-08-25
> **SeijiSensei said:**
> How about rather than pasting graphics you explain the problem in English?

Talk about an attitude problem. 

My post contains zero graphics, but you're quick with an attitude instead of clicking the links to see for yourself.

My post was also in English.

---

### Post by SeijiSensei on 2015-08-25
I don't think asking you to give a one or two sentence explanation for the problem is an "attitude problem." You present a bunch of stuff and expect us to figure out what you're asking?

So is the problem that you want to have a bunch of virtual interfaces, and they are not working?

Are you running a iptables firewall?  Have you permitted traffic to the entire subnet?

---

