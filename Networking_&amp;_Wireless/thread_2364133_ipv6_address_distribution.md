---
title: "ipv6 address distribution"
date: 2017-06-19
forum: Networking &amp; Wireless
---

### Post by tulpix2 on 2017-06-19
Hello

I have a problem with ipv6 addresses.
I have some bridges on my server which are used by different vms and belong to different vlans.

I used manual configuration in /etc/network/interfaces to give no ipv4 address to the bridge on the host, to prevent interaction with the host.
```

auto brwan
iface brwan inet manual

```

This works without a problem. But the interface still gets an ipv6 address.
I thought at first this was because i did not include any configuration for ipv6 so i included
```
iface brwan inet6 manual
```
and expected the same behavior for ipv6 but i still have 1 scope:local address and multiple scope:global addresses.

The full configuration for this bridge is
```

auto brwan
iface brwan inet manual
bridge_ports bond0.50
bridge_stp off
bridge_fd 1
bridge_maxwait 0
iface brwan inet6 manual

```

Has anybody an idea how i should adjust my config so my bridges don't get any ip addresses at all ?

Thanks in advance for any help.

---

