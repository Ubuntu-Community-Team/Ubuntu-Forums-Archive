---
title: "OpenVPN Routing Issue"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by LEMONed on 2008-11-27
I've managed to get OpenVPN running from the command line (network-manager doesn't work with it) and also set up the client to use the dhcp options pushed to it. For the record, making sure these lines are in your client.conf:

```
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf
```

You'll also need to install resolvconf with:

```
apt-get install resolvconf
```

This allows Ubuntu to use whatever dns/domain search options that have been passed over.


What I'm now looking to do is to mimic a similar option to the previous kde network manager which was to not route over a certain domain (in my case, my university domain). I know the IP and subnet I don't want to route over, so how would I automate this from the command line?

---

