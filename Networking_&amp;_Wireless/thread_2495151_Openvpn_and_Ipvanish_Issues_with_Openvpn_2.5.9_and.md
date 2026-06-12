---
title: "Openvpn and Ipvanish Issues with Openvpn 2.5.9 and Higher in 22.04"
date: 2024-02-08
forum: Networking &amp; Wireless
---

### Post by promet on 2024-02-08
After a recent update to 22.04 my, usually rock solid, ipvanish connection was losing internet connectivity.

It would authenticate and connect normally, but after about five minutes all connectivity was lost. There would be no error in the interface, it would just hang.

Once the ipvanish connection was terminated, all network service would resume as normal.

It turns out the .ovpn files ipvanish uses for vpn config contain a now deprecated line entry, which is:

```
keysize 256
``` 

This line must be removed from the .ovpn file entirely.

Here is a link to the ipvanish support page:

 '  **OpenVPN not working in Linux/Windows OpenVPN Client** '

[https://support.ipvanish.com/hc/en-us/articles/12976094099867-OpenVPN-not-working-in-Linux-Windows-OpenVPN-Client](https://support.ipvanish.com/hc/en-us/articles/12976094099867-OpenVPN-not-working-in-Linux-Windows-OpenVPN-Client)

I just thought I would share this here, because it took me a little while to stumble on this very simple fix and it would be good if I could save someone else that time.

best,

---

### Post by promet on 2024-02-09
CAVEAT:

lol, while my ' solved ' condition did help a lot. but openvpn is still quite wonky in 22.04.3.

it seems like there are still some ' gremlins ' in this scenario but, again, much better...

---

