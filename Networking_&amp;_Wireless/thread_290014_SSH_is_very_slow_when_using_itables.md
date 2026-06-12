---
title: "SSH is very slow when using itables"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by burni on 2006-10-31
Hello

On my ubuntu server (version 6.06) I've iptables configured. It works all. But when I'm connecting via ssh I've to wait a long time until I can do something. It's just via ssh. For http or ftp requests I have no delay.

Here is a dump of my configuration:

```

*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [395:101744]
-A INPUT -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT 
-A INPUT -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT 
-A INPUT -i eth0 -p tcp -m tcp --dport 21 -j ACCEPT 
-A INPUT -i eth0 -p tcp -m tcp --dport 20 -j ACCEPT 
-A INPUT -i eth0 -p udp -m udp --dport 53 -j ACCEPT 
-A INPUT -i eth0 -p tcp -m tcp --dport 53 -j ACCEPT 
-A INPUT -p tcp -m multiport --dports 49152:65534 -j ACCEPT 
-A INPUT -j DROP 
COMMIT

```

Could anybody help my?

Thanks

burni

---

