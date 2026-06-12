---
title: "OpenSwan, IPsec, &amp; Pluto"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by landonjh on 2007-08-09
Getting the following error message when running ipsec verify... any tips?

> Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                 [OK]
Linux Openswan U2.4.6/K2.6.20-16-server (netkey)
Checking for IPsec support in kernel                            [OK]
NETKEY detected, testing for disabled ICMP send_redirects       [OK]
NETKEY detected, testing for disabled ICMP accept_redirects     [OK]
Checking for RSA private key (/etc/ipsec.secrets)               [DISABLED]
  ipsec showhostkey: no default key in "/etc/ipsec.secrets"
Checking that pluto is running                                  [FAILED]
  whack: Pluto is not running (no "/var/run/pluto/pluto.ctl")
Two or more interfaces found, checking IP forwarding            [FAILED]
  whack: Pluto is not running (no "/var/run/pluto/pluto.ctl")
Checking for 'ip' command                                       [OK]
Checking for 'iptables' command                                 [OK]
Opportunistic Encryption Support                                [DISABLED]


---

### Post by john_navarro on 2007-08-15
I too am struggling with OpenSwan. I'd like to know how to restart IPSEC & PLUTO without rebooting the laptop. It's a shame it's this difficult to set up VPN.

---

### Post by Gustavo Orair on 2008-03-06
You have to problems that ipsec verify is telling you.
First of all the ipsec seems to not be up.
Try:
/etc/init.d/ipsec start

The second one is that the port Forwarding is disabled on this machine. Obviously if it is disabled it will not forward the "VPN" packets...

Edit file /etc/sysctl.conf and add the lines to enable IP Forwarding for ipv4 and ipv6:

# Enabling Ip Forwarding
net.ipv4.ip_forward = 1
net.ipv6.ip_forward = 1


I am supposing that you are using certifies to ensure the security of the VPN and then I am ignoring the error:
Checking for RSA private key (/etc/ipsec.secrets) [DISABLED]

---

