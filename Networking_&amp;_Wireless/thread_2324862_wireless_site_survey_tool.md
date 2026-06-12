---
title: "wireless site survey tool"
date: 2016-05-17
forum: Networking &amp; Wireless
---

### Post by koaung2 on 2016-05-17
I'd like to know Which software is the best for wireless site survey software in Ubuntu ?

---

### Post by SeijiSensei on 2016-05-17
I don't know what constitutes a "site survey," but nmap will poll all the machines in a network, identify their operating systems, and list any open ports on each one. The command

```
sudo nmap -A 192.168.1.0/24
```

produces a very extensive report on every active machine in that subnet.

If you just want to list the details of any visible wifi access points in your vicinity, use iwlist:

```
iwlist scanning
```

---

