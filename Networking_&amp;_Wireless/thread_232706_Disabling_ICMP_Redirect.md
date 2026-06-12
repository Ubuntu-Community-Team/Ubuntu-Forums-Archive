---
title: "Disabling ICMP Redirect"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by jimmy_k on 2006-08-09
Hello,

I have the following set up

1 linux box on 192.168.1.77 (mask 255.255.0.0; the router is the default gw)
1 wireless router on 192.168.0.2 (mask 255.255.0.0)
1 Ubuntu box on 192.168.0.3 (mask 255.255.255.0; the router is the default gw)

I want the ubuntu box to redirect all traffic via the router.

When I ping the linux box (192.168.1.77) from the ubuntu box it works the first time via the router and then gets an ICMP redirect host. This redirect presumably tells the ubuntu box to use a different - but it cannot find one and subsequently I cannot ping the linux box.

Is it possible to get the ubuntu box to ignore the redirect message and carry on regardless with the route using the router (I know there will be a slight performance hit)

I have tried the following two configuration changes but these made no difference (either pre or post reboot

(i) Editing /etc/sysctl.conf and adding net.ipv4.conf.all.accept_redirects = 0

(ii) Running the commands:
     /bin/echo "0" > /proc/sys/net/ipv4/conf/all/accept_redirects
     /bin/echo "0" > /proc/sys/net/ipv4/conf/all/secure_redirects
     
Any help would be greatly appreciated.

---

