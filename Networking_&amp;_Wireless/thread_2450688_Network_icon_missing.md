---
title: "Network icon missing"
date: 2020-09-18
forum: Networking &amp; Wireless
---

### Post by toyduh on 2020-09-18
Hi

i had some troubles starting with my desktop graphics, so I reinstalled gdm3 and then ubuntu-desktop again. Something went wrong on the networking on the way.
- When Ubuntu loads there is no networking icon at the top right
- Network is not connected. 

I can connect manually using `ifconfig enp2s0 up` followed by `dhclient -r enp2s0` and `dhclient -r enp2s0` (as done here [https://askubuntu.com/questions/1025008/ipv6-is-working-but-ipv4-isnt](https://askubuntu.com/questions/1025008/ipv6-is-working-but-ipv4-isnt))
This is working, but I need to do it again after each reboot. How I set it to automatically connect after reboot?

I also tried setting `managed=true` in the NetworkManager.conf but it had no apparent effect.

thanks

---

