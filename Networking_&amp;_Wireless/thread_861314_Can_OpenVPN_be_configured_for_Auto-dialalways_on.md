---
title: "Can OpenVPN be configured for Auto-dial/always on?"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by jnorth on 2008-07-16
I currently have OpenVPN configured and working wonderfully - fast and secure between a few clients and a central network.

What I would like to do is have the clients (on latest Ubuntu) always stay connected to the VPN.  If they switch to wireless, it should redial, if they change networks, it should redial, etc - whatever it has to do to try to maintain connectivity.

The reason?  Reverse connectivity no matter where the clients are (i.e. if they aren't behind a personally or company-controlled firewall that can have NAT rules added).

We'll be using it it mainly for ssh and NX access back into the machines, sort of like a logmein kind of thing.  It works perfectly now, except for the fact that the clients have to manually connect the VPN anytime we need access - I'd like to automate that.

Thanks!

---

