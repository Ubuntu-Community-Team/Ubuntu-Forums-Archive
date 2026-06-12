---
title: "Internet very slow and dropping Dell xps13"
date: 2020-07-06
forum: Networking &amp; Wireless
---

### Post by yassatoubab on 2020-07-06
Hi

I bought a new Dell xps13 in December and installed Ubuntu 19.10.
I had some internet problems from the start, but they were minor. By March the problems seemed worse but by then I thought I'd wait for Ubuntu 20.04.

I successfully upgraded but the internet problems remained. 
These days I have to load most pages twice because they time out the first time. The internet also keeps dropping. I have to turn the network off and then on again. With luck I can load 2 or 3 pages and then it is gone again.

I hope someone can tell me what is wrong and what I can do about it.

Thank you!

---

### Post by praseodym on 2020-07-06
Lets try

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by yassatoubab on 2020-07-08
I have done as you suggested. The connection is much improved. Since making the changes yesterday I have had only one time-out.
Thank you very much.

---

