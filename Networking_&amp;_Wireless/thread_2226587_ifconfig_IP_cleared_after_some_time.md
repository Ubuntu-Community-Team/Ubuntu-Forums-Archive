---
title: "ifconfig IP cleared after some time"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by Kleenux on 2014-05-28
Occasionally I need to set my eth0 (wired) to a specific IP address, eg

```
ifconfig eth0 192.168.100.2/24
```

while connected to a device for instance, which does not provide DHCP.

This works ok, and "route" is set as well automatically.
However after a few minutes, eth0 is automatically reset back to no IP... (and the route is removed).

[LIST]
[*] there is nothing in /etc/network/interfaces concerning eth0
[*] NetworkManager does have eth0 as DHCP in its own config
[*] doesn't happen if I "force" the IP in /etc/network/interfaces
[*]
[/LIST]

My guess is that networkmanager doesn't care if an IP is set in eth0, check "interfaces" and reset eth0 if DHCP is not available?

It is annoying as I want to set IPs depending on device to eth0 quickly, without having to set "interfaces" all the time.

- is network manager guilty? and do you recommend in this case to remove eth0 from NM?
- maybe another attribute to "ifconfig" would allow eth0 to keep its IP for a long time?
(until next boot / next ifconfig)

---

### Post by mohammad_ali2 on 2014-05-28
I am not a  guru but You can remove the network manager, this is what many professionals do they force an IP in the etc/network/interface file. By the way network manager is bypassed when you give a static IP it do not interfere.

---

### Post by Kleenux on 2014-05-28
Thanks - but we all know NM can be removed ;-)
I was more expecting an enlightened explanation of why NM would do that / is there a way to configure it not to do that (since there is an IP why would it clear it?!).
And "is removing NM *recommended*"?

---

