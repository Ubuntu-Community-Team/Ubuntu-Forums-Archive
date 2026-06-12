---
title: "iptables question"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by ==Troy== on 2008-08-01
I would like to only allow certain set of ips to be available to a user to connect to the internet.

Currently one of those allowed ips is a dynamic (another pc) and can be accessed by a dns request, but since it is insecure to allow dns lookups for iptables, and hence, I want to make an AND condition for the iptables. Resulting in the condition where the dns lookup result is compared to the subnet(e.g. if example.no-ip.com && 76.12.2.4/16 ALLOW).

How can that be done?

Second question is the per-user incoming traffic block. It is possible to block outgoing traffic by the user id, but will that work for the incoming traffic as well?

Thank you in advance.

---

