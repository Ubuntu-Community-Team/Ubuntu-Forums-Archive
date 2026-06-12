---
title: "Disable IPV6"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by weaver4 on 2008-05-31
How do I disable IPV6?

---

### Post by pacrep on 2008-05-31
At the end of the page add this: blacklist ipv6

```
sudo gedit /etc/modprobe.d/blacklist
```

---

### Post by darco on 2008-05-31
then run this command to confirm:

```
ip a | grep inet6
```

good luck
darco

---

### Post by kerry_s on 2008-05-31
in terminal:

sudo -i
echo "alias net-pf-10 off" > /etc/modprobe.d/blacklist_ipv6

---

