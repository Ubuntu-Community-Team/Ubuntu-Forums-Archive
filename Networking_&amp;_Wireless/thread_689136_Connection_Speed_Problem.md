---
title: "Connection Speed Problem"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by 02lancastr on 2008-02-06
Hi im fairly new to linux, ive used the live CDs for a while but finally decided to stick with ubuntu 7.10 =D
Im only just getting used to the terminal and ive got the OS how i like it, apart from one thing. My connection speed.

Ive always had a problem with my NIC, even when i used to use windows. But i fixed this by turning my connection speed down to 10mbps half duplex.
 Tbh i had no idea what it did but is seemed to work. but i down know what im doing on ubuntu, ive tied a few terminal commands i found in the forum but to no sucess.

Please help
Btw im using a ehternet connection to a BT home hub router/modem. On a realtek NIC, sorry unsure of the product code at the moment. Currently at school. 

Thanks in advance

---

### Post by jan quark on 2008-02-06
when you're back home run this commands to specify your nic

```
lshw -C network
```

```
lspci
```
```

iwconfig
```
```

sudo iwlist scan
```

---

