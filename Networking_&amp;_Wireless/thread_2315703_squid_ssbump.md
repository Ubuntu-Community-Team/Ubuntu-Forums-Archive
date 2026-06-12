---
title: "squid ssbump"
date: 2016-03-01
forum: Networking &amp; Wireless
---

### Post by bmahak2005 on 2016-03-01
I have installed squid 3.15 on ubuntu 15.10 server.
squid was setup with sslbump for https traffic.
The functionality work without any problem i.e. : all traffic from both http and https goes through squid and all internet can be accessed
on all devices where certificates are installed.
With one exception : 'Netflix APP' no longer works on IOS devices (iPhone, iPad). no matter what I do. All other internet services (safari, and other apps) work properly on those devices.
And I was able to run Netflix from browser on linux boxes and even OS X safari. The only thing that is not working is Netflix APP on IOS.

Of course if I disable sslbump and only allow http to go through squid netflix works.
I tried both transparent mode and proxy mode on the iPhone, still not working.

Did anyone manage to make Netflix APP on IOS devices work with squid with sslbump enabled ?

HB.

---

### Post by SeijiSensei on 2016-03-02
If you're using transparent proxying via an iptables rule, you could just add a rule that avoids the proxy for connections to netflix.com.  First we need the list of Netflix hosts:
```

$ host netflix.com
netflix.com has address 54.243.253.96
netflix.com has address 75.101.139.66
netflix.com has address 107.20.151.133
netflix.com has address 107.20.154.246
netflix.com has address 107.20.177.34
netflix.com has address 174.129.2.58
netflix.com has address 23.21.190.124
netflix.com has address 23.23.191.68
netflix.com has address 50.19.210.42
netflix.com has address 54.204.2.219
netflix.com has address 54.204.43.31
netflix.com has address 54.225.192.83

```

Now for each host you would add
```

/sbin/iptables -t nat -A PREROUTING -s your.local.sub.net/mask -d 54.243.253.96 -p tcp --dport 443 -j ACCEPT
[etc.]

```
Put all these rules ahead of the default REDIRECT to the Squid port.

---

