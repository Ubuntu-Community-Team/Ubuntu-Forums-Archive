---
title: "Hosting services using ipv6 IP addresses - What am I doing wrong?"
date: 2017-08-24
forum: Networking &amp; Wireless
---

### Post by icsy7867 on 2017-08-24
So I am pretty new to IPv6 and I am trying to learn the basics.  My ISP does not offer a public IPv4 address, but offers basically whatever IPv6 addresses you would want.  So I enabled "Native" ipv6 in my router and my boxes who have ipv6 enabled get a public IPv6 address.  Traffic to these machines are handled by my routers IPv6 firewall and their local firewalls as well.  So far so good... but here is where things get weird.

Firstly I am pretty sure i have things setup correctly.  I have a windows box with [Win_ipv6_address] and I enabled port 3389 (I do not support external RDP traffic, but it is a good test).  This works flawless.  I can RDP into my windows box and it has yet to not work.  It seems to work pretty well and without issue.

Now we come to my freebsd Jails and ubuntu devices.  I cannot seem to get these to work reliably and I think there is a setting I am forgetting or something:
I enabled
```

[COLOR=#000000][FONT=Arial]net.ipv6.conf.all.disable_ipv6 = 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]net.ipv6.conf.lo.disable_ipv6 = 0[/FONT][/COLOR]

```

and I was playing around with:
```
[COLOR=#000000][FONT=Arial]net.ipv6.conf.all.forwarding=1[/FONT][/COLOR]
```

But I found that when I enabled this on my ubuntu box, the device no longer received an IPv6 global address.  Not even really sure if this is needed to be honest.

Moving on... On one of my machines, I am hosting owncloud.  Currently I use my router to connect to a VPN provider that allows port forwarding, and I allow access through this but it can be slow.  Internally I can access the Owncloud instance by connecting to [https://](https://)[owncloud_ipv6_address] and not have any issues.  Externally... it works... SOMETIMES.  The few times I have gotten it to work, I grabbed an ISO file and it maxed out downloading around 500-800 KB/s (I get 2-3 MB/s through my paid vpn tunnel).

So I am thinking thinking that the issue must be something in the OS since my windows host does not seem to have a problem.  I also tried changing the apache conf to ports > 50000 just in case my ISP was throttling HTTPS or something weird like that but I had the same result.  I have been racking my brain over this and thought that perhaps some more experienced than I knew of something that I had missed. Thanks for checking!

---

