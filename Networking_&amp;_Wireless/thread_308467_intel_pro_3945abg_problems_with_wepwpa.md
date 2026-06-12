---
title: "intel pro 3945abg problems with wep/wpa"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by suoko on 2006-11-28
hi,

I have the intel pro 3945abg wireless nic in my notebook and I have problems with the wep encrypted networks.

1) network-admin:
I doesn't show any network names but if I manually insert the network name it works - although the network MUST NOT be encrypted.

2) network-manager:
It seems working with wep/wpa but not completely. I'm trying connecting to my fonera AP and it doesn't start browing. It connects to the network but then shows the fonera admin page instead of letting me browse.
However network-manager seems to be broken: sometimes it works, sometimes not. And it messes up network-admin

Any solution out there?

---

### Post by suoko on 2006-11-28
problem solved.

I had to disable all network cards in network-admin, set the encryption to wep in the fonera AP and then use network-manager.

Comment:

Let's get rid of network-admin as soon as network-manager will be able to set a static IP !!

---

