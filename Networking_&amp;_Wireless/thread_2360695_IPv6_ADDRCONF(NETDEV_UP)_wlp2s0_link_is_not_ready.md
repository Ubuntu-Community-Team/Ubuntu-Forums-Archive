---
title: "IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready"
date: 2017-05-07
forum: Networking &amp; Wireless
---

### Post by phileconte on 2017-05-07
Hi,
on my Asus ZENBOOK, start-up is long due to 
```
[    6.732645] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
```
which finally become ready at 24 sec
```
[   24.172449] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
```
after an Internet search, I wonder if the error might be due at the two following lines :
[    6.733008] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    6.733450] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled

is it possible that there is a conflict and why the interface is declared two times ?
 DMESG is attached,
Thanks for your help

---

### Post by chili555 on 2017-05-07
Network Manager is trying to get an IPv6 address for you. It tries, it waits, it tries some more and then bails out. Your ISP may or may not offer IPv6 addresses, Your DSL or cable modem may or may not be capable of IPv6. 

You could certainly ask NM to stop trying: [https://farm8.staticflickr.com/7293/16394993017_21917f027b_o.png](https://farm8.staticflickr.com/7293/16394993017_21917f027b_o.png)

These lines are normal and not relevant to the issue:> [ 6.733008] iwlwifi 0000:02:00.0: L1 Enabled - LTR EnabledThey are produced in abundance in my machine that boots in about 7 seconds and does get IPv6 addresses.

---

### Post by pabloab7772 on 2017-06-07
Same here with Asus Zenbook UX303UB: Syslog:

[HTML]kernel: [ 9497.495649] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready[/HTML]

On BIOS CMOS setup, network section, you have IPv4 enabled but IPv6 disabled.

---

