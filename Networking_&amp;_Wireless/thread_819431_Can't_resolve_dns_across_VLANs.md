---
title: "Can't resolve dns across VLANs"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by Torchnw on 2008-06-05
Doing a project at school, we've set up 2 boxes running ubuntu hardy server.

One is functioning strictly as a router running iptables and dhcp-services, and the other is running samba and bind9 dns server. We've also installed Webmin 1.420 for easier administration.

The router has 2 NICs where eth0 is the wan interface and eth1 is the raw device for for a series of vlans.

Now if we try to ping a domain name ( like google.com ) from the samba/dns-box, it works just fine. If we ping google.com from another computer on the same vlan, that works too, but if we move that other computer to a different vlan, it doesn't work anymore. You CAN, however, ping the samba/dns-server itself from the other vlan, it just won't resolve domain names. :confused:

We tried to open up everything in iptables ( all chains have default policy set to ACCEPT ). Everything else works. We've even managed to join a WinXP computer to the samba domain across vlans. 

I'm coming up short on things to try, so I would really appreciate some input or ideas of what to do next. ](*,)

Thanks in advance

---

### Post by derelict888 on 2008-09-15
I am also having strange DNS issues. I can ping in a terminal using a dns name, I can do nslookup in terminal and get the IP of the machine. However if I try using the DNS of a local server to access say our wiki or other internal web-based stuff, I get unable to connect. If I put in the IP, no problem. I have checked my DNS settings and they're pointed at our 2 nameservers. Any ideas? Is this just a bug or do I have something set wrong?

---

