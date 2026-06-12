---
title: "internet sharing (routing and forwarding, iptables)"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by kane77 on 2007-01-13
I have set up a internet sharing with iptables:
```
iptables --flush
iptables -t nat --flush
iptables --delete-chain
iptables --table nat --delete-chain
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
iptables --append FORWARD --in-interface eth1 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward
```

BUT it only works when I log in.. how do I make it work on the login screen (without anybody logged in)... I would want to start the computer with wake on lan and use the internet rightaway...

---

### Post by kane77 on 2007-01-14
bumpy

---

### Post by koenn on 2007-01-14
in stead of running it at login, you could run it at startup by making it a startup script:

put the script in /etc/init.d
use update-rc.d to create the links that will make the script start at startup

---

### Post by kane77 on 2007-01-15
somebody said something about putting it into rc.local     how do I put it there??

---

