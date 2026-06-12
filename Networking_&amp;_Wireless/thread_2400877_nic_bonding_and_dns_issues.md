---
title: "nic bonding and dns issues"
date: 2018-09-11
forum: Networking &amp; Wireless
---

### Post by mattdawolf on 2018-09-11
I can get the bonded connection to work but very soon after it activates, dns tends to stop working and nothing can find a route to host. I am a newbie with bonding connections. I am running 18.10

```


# interfaces(5) file used by ifup(8) and ifdown(8)
auto bond0       
iface bond0 inet static
hwaddress 0c:c4:7a:b5:7d:76
address 10.0.0.3
netmask 255.0.0.0
gateway 10.0.0.1
dns-nameservers 9.9.9.9 77.88.8.8 10.0.0.1
dns-search domain.local
slaves enp4s0f0 enp4s0f1 enp131s0f0 enp131s0f1 enp132s0f0 enp132s0f1 enp133s0
bond_mode 0
bond-miimon 100
bond_downdelay 200
bound_updelay 200

```

---

### Post by #&amp;thj^% on 2018-09-11
**Just pointing out**>> 18.10 is in a Development Version (Point Release) so keep this in mind.:)
From what I've read, we just need to add dns-nameservers into /etc/network/interfaces
Do you have it added to "/etc/network/interfaces"
**_I don't why I did not see your " /etc/network/interfaces" code when I first looked on this thread_. (So the below is useless to you)**
```
dns-nameservers 9.9.9.9 77.88.8.8 10.0.0.1
```

EDIT: Forgot to add restart:
```
sudo systemctl restart networking.service
or
sudo ifdown eth0 && ifdown eth1 && ifup bond0
```
Use the correct naming for eth0 and eth1

---

