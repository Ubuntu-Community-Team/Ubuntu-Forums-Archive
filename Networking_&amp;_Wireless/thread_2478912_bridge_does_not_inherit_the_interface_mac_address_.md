---
title: "bridge does not inherit the interface mac address on 22.04"
date: 2022-09-08
forum: Networking &amp; Wireless
---

### Post by mboukhalfa on 2022-09-08
Hey,

on ubuntu 20.04 the bridge clone the interface mac address when doing : 
```

sudo brctl addbr br0
sudo  ip link set br0 up
sudo  brctl addif br0 eth2

```
but on the ubuntu 22.04 the bridge got new generated mac !
Is this an issue or an expected behavior ? 
if so what exactly changed and how I can revert the 20.04 behavior so the bridge just take the first attached interface mac address

---

### Post by mboukhalfa on 2022-09-09
Change the **macaddresspolicy** in **/usr/lib/systemd/network/99-default.link** 
It has been changed in 22.04 to **persistent** changing this to **none** option will revert the previous behavior so the bridge will clone the first interface attached mac.
Check: [https://www.freedesktop.org/software/systemd/man/systemd.link.html#Examples](https://www.freedesktop.org/software/systemd/man/systemd.link.html#Examples)

---

