---
title: "dhcp server &amp; ipforward"
date: 2017-04-17
forum: Networking &amp; Wireless
---

### Post by jimmi1972 on 2017-04-17
[SIZE=4]Hi
I have a desktop Ubuntu with 2 network interfaces:
enp4s1 - connected to the internet via router (dfgw - 10.0.0.138) enp3s0 - need it as a dhcp server 
a. how do I set a dhcp server from enp3s0 network interface? 
b. how can I config ipforward so that all traffic from enp3s0 will go threw enp4s1 (to the internet www and back...)
Thanks ahead - Jimmi
[/SIZE]

---

### Post by SeijiSensei on 2017-04-17
1)  Install the isc-dhcp-server package.  Then edit /etc/default/isc-dhcp-server and change the INTERFACES line to read
```
INTERFACES="enp3s0"
```

2) Read this: [https://help.ubuntu.com/community/Internet/ConnectionSharing#Simple_iptables_example](https://help.ubuntu.com/community/Internet/ConnectionSharing#Simple_iptables_example)

---

### Post by jimmi1972 on 2017-04-18
**[SIZE=3]Tnx![/SIZE]**
[SIZE=3]and after how do I make the packets from enp3s0 go threw enp4s1?[/SIZE]

---

### Post by SeijiSensei on 2017-04-18
It's all explained in (2) above.  Basically you need to enable packet forwarding in /etc/sysctl.conf and add a couple of iptables rules to "masquerade" your outbound traffic.

---

### Post by jimmi1972 on 2017-04-18
Tnx

---

