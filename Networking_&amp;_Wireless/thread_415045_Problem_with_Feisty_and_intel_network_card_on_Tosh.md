---
title: "Problem with Feisty and intel network card on Toshiba Satellite"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by nozey on 2007-04-20
I have Kubuntu Edgy working great on my Toshiba Satellite Laptop. Now im trying to install Kubuntu Feisty. The problem is that i cant configure my network card. Heres the one:

```
$ lspci | grep -i ethernet
00:0a.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
```

Module **e100** is up.

I run :

```
ifconfig eth0 x.x.x.x netmask x.x.x.x up
route add default gw x.x.x.x
```

And its ok. **ifconfig** shows my network configuration. The problem is that when i run **mii-tool** i get:
```

eth0: no link
```

**The link is ok**. Im sure of it. When i boot with edgy it works ok. I tryed the same network cable on another machine and it works too.

So ... any sugestions?

---

