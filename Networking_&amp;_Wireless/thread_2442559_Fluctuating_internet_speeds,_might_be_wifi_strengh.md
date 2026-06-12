---
title: "Fluctuating internet speeds, might be wifi strenght? Lubuntu 19.10"
date: 2020-05-04
forum: Networking &amp; Wireless
---

### Post by rosco0 on 2020-05-04
Hello first time poster and also Ubuntu noob. Some help would be greatly appreciated.

When I am next to my router I get around 40mbps speed, but when I go to another room my speed fluctuates frequently. It ranges from less than 1mbps to 10mbps. Could it be fixed with a terminal command regarding wifi strenght? 

I also tried installing drivers as explained in the sticky thread but I get no output when I enter 
```
lspci -nn -d 14e4:
```

The following codes were succesfully ran as well:
```
sudo apt update
sudo apt dist-upgrade
```

Thank you in advance!

---

### Post by chili555 on 2020-05-04
Please start by removing the incorrect driver:

```
sudo apt purge bcmwl-kernel-source
```

Reboot and tell us if there is any improvement.

---

### Post by rosco0 on 2020-05-04
Thanks for taking the time to reply back Chili,

I have ran the purge code and rebooted. Speeds are still varying from 1mbps to 10mbps. My connection speed is 60mbps..

---

