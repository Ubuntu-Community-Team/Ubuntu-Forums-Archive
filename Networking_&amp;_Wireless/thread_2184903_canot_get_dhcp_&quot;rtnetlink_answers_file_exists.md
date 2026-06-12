---
title: "canot get dhcp &quot;rtnetlink answers: file exists&quot;"
date: 2013-10-31
forum: Networking &amp; Wireless
---

### Post by ikki_72 on 2013-10-31
my eth0 configured with static IP

when connected to another network, I ran 'sudo dhclient eth0' to get IP from said network temporarily but IP isn't changed.

I tried killing dhclient process with 'sudo kill -9 PID' and still same.

Ubuntu Server 12.04.3 32-bit

---

### Post by alivema4ever on 2013-10-31
Do you mean to get an ip address assigned automatically by 'another network'
If so, you must set eth0 as dchp client. Remove any static configuration you've made before.

Config file: /etc/network/interfaces
```
auto eth0
iface eth0 inet dhcp
```

Then you can try flushing ip address on eth0, then running dhclient afterwards.

```
sudo ip link set eth0 down
sudo ip addr flush eth0
sudo ip link set eth0 up
sudo ifup eth0
```

Look at the result.

---

