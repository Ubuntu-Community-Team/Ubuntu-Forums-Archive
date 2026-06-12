---
title: "iwconfig doesn't show wireless IF as NM use it"
date: 2019-12-18
forum: Networking &amp; Wireless
---

### Post by tootai on 2019-12-18
Hello,
on an 18.04 up to date notebook, I try to not use NM but systemd-networkd for both network interfaces, enX and wlX. As it's OK for enX (bridged as lan IF), I'm unable to get wlan0 up (wlX is renamed in wlan0): iwconfig tells no wireless extensions (!) as NM is able to use it. Even when NM is taking care of the wireless interface, iwconfig complains with no wireless extensions.

Also, when NM is not involved, "ip a" shows wlan0 but down. ifconfig wlan0 up does nothing. I don't use ifupdown.

Note: to tell to NM to not take care of the interfaces, I put their MAC address as unmanaged in conf file.

Does someone have an idea on whats happend and how to solve this ?

Thanks for any hint

Daniel

---

### Post by praseodym on 2019-12-20
Please run the wireless script from the sticky thread and show the outputs

---

