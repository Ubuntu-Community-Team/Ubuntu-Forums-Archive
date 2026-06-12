---
title: "dnsmasq to block internet connected device and redirect to internal IP"
date: 2018-07-12
forum: Networking &amp; Wireless
---

### Post by lucas001 on 2018-07-12
I have an internet connected device (on 192.168.1.103) which communicates with a webserver (externalwebserver.is).  

I want to redirect the device to IP 192.168.1.107 on which I have an nginx server with a flask application.

As the router doesn't let me do the redirection I have tried to implement DNS routing using dnsmasq.  

I have added 192.168.1.107 to the DNS section of DHCP settings in the router and set up dnsmasq as per below:

```
domain-needed
bogus-priv
no-dhcp-interface=
strict-order
cache-size=1000
localise-queries

server=127.0.0.1
#server=8.8.8.8

address=/externalwebserver.is/192.168.1.107
address=/www.externalwebserver.is/192.168.1.107
listen-address=127.0.0.1
listen-address=192.168.1.107
interface=enp7s0

no-hosts

log-facility=/var/log/dnsmasq.log
log-queries
```

After implementing the above dnsmasq settings, when I access [http://externalwebserver.is](http://externalwebserver.is) I get the flask application's response from 192.168.1.107 which is what i expect.  I can also curl GET and PUT to the webserver via [http://externalwebsever.is](http://externalwebsever.is) successfully and it hits my flask application as expected.  All good so far.

However, the device continues to make it's way through to the actual external webserver - no matter what settings I use in dnsmasq, I cannot successfully block it from accessing the internet. 

Any ideas on why this is just not working for me?

---

