---
title: "SSHD_CONFIG ListenAddress"
date: 2016-07-02
forum: Networking &amp; Wireless
---

### Post by S.User on 2016-07-02
Hello,

I'm configuring my sshd_config.

However the man page doesn't make it clear enough, so I'd like to reconfirm:

The ListenAddress (if restricted) would be the default gateway to the router but not the IP it received from the router I believe...?
If it's listening, it can only come from the router gateway, I'd assume, correct?

Stephan

---

### Post by steeldriver on 2016-07-02
AFAIK it is the IP(s) of the machine's own interface(s) (whether received from a router, or configured statically)

The defaults are 0.0.0.0 for IPv4 or :: for IPv6, representing "any interface"

AFAIK setting it to a specific (restrictive) IP only has value when your machine has multiple interfaces / multiple IP addresses configured (for example, if the machine itself is a gateway, you could allow SSH via the LAN-facing interface, but not from the WAN)

What exactly are you trying to achieve? If you want to blacklist / whitelist IPs for SSH you can do that via firewall rules (either using iptables or via ufw)

---

