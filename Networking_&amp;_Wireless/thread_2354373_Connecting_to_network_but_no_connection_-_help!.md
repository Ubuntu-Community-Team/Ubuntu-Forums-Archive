---
title: "Connecting to network but no connection - help!"
date: 2017-03-02
forum: Networking &amp; Wireless
---

### Post by nikos_ubu on 2017-03-02
dear forum,

i've messed up my ubuntu configuration big time. I had dansguardian + privoxy running nice and smoothly, until after a freeze I rebooted and could not connect to internet anymore. I've removed dansguardian, privoxy, tinyproxy, firehol, resetted the iptables rules to the default ones. Under my system settings --> Network --> Proxy is set to None. Firefox also uses no proxies. I connect to wifi normally but nothing happens after that. For instance, apt-get update stucked at 0% and no further messages appear.

I'm using Ubuntu 14.04 w. 4.4.0-64.

Any help is greatly appreciated.

---

### Post by TheFu on 2017-03-02
Restore from the backup made prior to making the huge changes.

For troubleshooting normal networking, [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) explains some steps. Be certain to change any IP addresses to those that your specific network needs.

---

