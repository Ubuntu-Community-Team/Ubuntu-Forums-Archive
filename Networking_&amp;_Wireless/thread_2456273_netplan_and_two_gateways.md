---
title: "netplan and two gateways"
date: 2021-01-08
forum: Networking &amp; Wireless
---

### Post by ppisz on 2021-01-08
Hello!

I know this problem has been discussed more than once, but I need help.


I have two NICs, one is for mgmt (ens3) traffic and the other is for dmz (ens6):

```

network:
  version: 2
  renderer: networkd
  ethernets:
    ens3:
      dhcp4: no
      addresses: [10.88.2.222/23]
      gateway4: 10.88.3.254
      nameservers:
              search: [cenagis.local]
              addresses: [10.88.2.211,10.88.2.212,10.89.12.213]
    ens6:
      dhcp4: no
      addresses: [10.88.12.7/24]

```


If I manually enter the second routing route, everything works perfectly:

```

ip route add 10.88.12.0/24 dev ens6 src 10.88.12.7 table rt2
ip route add default via 10.88.12.254 dev ens6 table rt2
ip rule add from 10.88.12.7/32 table rt2
ip rule add to 10.88.12.7/32 table rt2

```

However, I can't do this on a netplan, can someone help me translate these commands into a netplan?

Best regards!

---

### Post by TheFu on 2021-01-08
Nobody can help until you edit the post above and use "code-tags" so all the indentation is corrected.
[https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

---

### Post by ppisz on 2021-01-09
Corrected, sorry :)

---

### Post by TheFu on 2021-01-09
```
ip route | column -t
```
before it works AND after it works?
Please.

Did you try adding the  gateway4: xx.xx.xx.xx   for rt2 in the     ens6: stanza?

---

