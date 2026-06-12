---
title: "Problems with internetconnections on kUbuntu 6.06 LTS"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by Ulyssus on 2006-08-27
Hello,
since 2 days I've got kUbuntu 6.06 LTS and since then the internet is not working. Maybe it's a problem with my Ethernet Card:
```
0000:00:07.0 Ethernet Controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```
So, i found this one: [http://www.ubuntuforums.org/showpost.php?p=1416012&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1416012&postcount=6)
Now, I want to know, is this working or not?

---

### Post by daller on 2006-10-05
I assume it WIRED ethernet, not wireless?

Please go to a terminal, and give me the output from the 2 following commands:

```
sudo ifdown eth0
```

and:

```
sudo ifup eth0
```

---

