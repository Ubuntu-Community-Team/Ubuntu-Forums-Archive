---
title: "Squid Server: Set Src and Dst IP"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by NagWolf on 2009-05-25
Hi there;
Been using a Suse server as Firewall, squid & squidGuard as well as load-balancing device.
I installed a MikroTik router now to serve as the Firewall and as the Load-balancing (DSL Bonding) device.
I upgraded (  :)  ) the squid server to Ubuntu Server 9.04 and just imported my current squid.conf & squidGuard.conf files.
As the old server had 3 NICs in it (1x Local, 2x Public) the squid.conf points to the Public acl IPs as the Source (Src) Gateways from which the content is downloaded, cached and forwarded to my clients (Dst).
Before I just go mad and change Config settings...
My Q: Should I configure the new server to use One Gb Lan port for all traffic, to Listen on port 3128 for requests on ip 10.10.10.10, which will come from the MikroTik router (10.10.10.14) and then to download the content via the same IP (10.10.10.14) which in it's turn will then make the content available via the Bonded two DSL IPs in the 196.x.x.x range?

I really hope this makes sense to someone and that someone on these forums has done this before... [-o<

---

### Post by NagWolf on 2009-05-25
No help please from anybody using Squid?

---

