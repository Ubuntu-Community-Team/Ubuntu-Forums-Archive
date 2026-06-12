---
title: "assign multiple IP adresses to one Ethernet port?"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by TheXenophobeist on 2010-04-27
Is there a way to assign multiple IP adresses to one Ethernet port?
On my XP Laptop I have a 10.0.0.-shceme & a 192.168.1.-scheme, both on one copper port, simultaneously. This allows me to ping & sweep both of those networks without having to keep changing it over. I havent been able to find where/how to set up the same advantage on my Ubuntu Machine yet.
 
Help anyone??

---

### Post by jvc26 on 2010-04-28
I have a feeling ifconfig can be used to do this:

```
ifconfig <interface> add
```

That creates you an interface like eth0:0 which you can then get a dhcp lease for.

```
dhclient <interface>
```

I'm not sure that all network cards support this, but its worth a shot.

J

---

