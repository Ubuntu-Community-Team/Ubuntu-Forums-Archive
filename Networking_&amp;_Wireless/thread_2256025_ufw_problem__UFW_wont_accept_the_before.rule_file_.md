---
title: "ufw problem : UFW wont accept the before.rule file for some strange reason!"
date: 2014-12-09
forum: Networking &amp; Wireless
---

### Post by kev9 on 2014-12-09
Hi,
I have tried to add the rules but ufw always rejects them. Below is copy of my before.rules file, the below is a section of the last part and the last line is COMMIT but for some reason ufw wont accept this. Could someone tell me why?


```
*nat
:POSTROUTING ACCEPT [0:0]
# Allow traffic from OpenVPN client to eth0
-A POSTROUTING -s 10.8.0.0/8 -o eth0 -j MASQUERADE


COMMIT
Hi,
I have tried to add the rules but ufw always rejects them. Below is copy of my before.rules file, the below is a section of the last part and the last line is COMMIT but for some reason ufw wont accept this. Could someone tell me why?

Part of /etc/ufw/before.rules

[code]
*nat
:POSTROUTING ACCEPT [0:0]
# Allow traffic from OpenVPN client to eth0
-A POSTROUTING -s 10.8.0.0/8 -o eth0 -j MASQUERADE


COMMIT


```


Really appreciate if someone can help me here!

Thanks

---

