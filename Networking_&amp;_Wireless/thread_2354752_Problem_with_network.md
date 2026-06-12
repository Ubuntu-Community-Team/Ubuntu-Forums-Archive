---
title: "Problem with network"
date: 2017-03-05
forum: Networking &amp; Wireless
---

### Post by djmixerno1 on 2017-03-05
I have a strange Problem.

My /etc/network/interfaces:
auto ens224
iface ens224 inet static
    address 888.95.xxx.xxx
    netmask 255.255.255.xxx
    gateway 888.95.66.xx
    dns-nameservers 8.8.8.8

Everything is right with my interfaces (the 888 is an example I know, that the max is 255), but now comes the problem:
If I am trying to ping websites it works, but I cant install any package or something else. I cant download anything.
Can anyone help? I also tried to reinstall

---

### Post by opsusec on 2017-03-06
run :~$ifconfig 
post result

run :~$netstat -i

post result, lackluster details generally blockade the simplest of solutions.

---

