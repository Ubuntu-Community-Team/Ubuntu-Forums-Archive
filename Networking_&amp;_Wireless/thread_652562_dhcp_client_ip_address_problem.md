---
title: "dhcp client ip address problem"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by subjam on 2007-12-28
Hi, All,

I have a Linux server running Debian Lenny. I had an annoying problem with
dhcp as follows: the server alternates between two ip addresses around every
hour (ip addresses are obtained via a dhcp server provided by the
university). This causes me a lot of trouble because I use ssh to access the
server: the change of ip address interrupts my ssh connection. I have to
reestablish the ssh connection using the right ip address every time it
changes. 

Actually, the school provides DNS service for dhcp clients. For example, you
can set up your machine with a hostname such as "name.dhcp.xxx.edu". The
weird thing with my server is that, it alternates between two ip addresses,
say, A and B. At any time, only one IP address is valid. However, if I use "host A"
or "host B", both of them give "name.dhcp.xxx.edu". If I use "host name.hdcp.xxx.edu",
it gives the IP address that is currently valid. So even I use the fixed hostname to
establish my ssh connection, I still have the problem.

Any thoughts will be appreciated.

---

### Post by mellowd on 2007-12-29
2 IP changes every hour? That would mean they have set the IP lease to only 30 minutes, which I think is far to little. You could ask them to increase their lease, maybe a week? Unfortunately this could be out of your control.

What kind of network device do you have? You could use a dynamic dns service that auto updates itself. For example, I have a hardware firewall and my IP lasts 7 days, I vpn into my home network. In order for the vpn to work I don't want to have to know the IP I have everytime, dyndns takes care of that automatically updating itself every 4 hours.

If you connect straight into a network socket you could set up dyndns with the server itself (though I myself have never done this, I know it is possible)

---

