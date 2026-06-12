---
title: "Missing /etc/default/tlp"
date: 2016-11-16
forum: Networking &amp; Wireless
---

### Post by Drate on 2016-11-16
I am trying to get Wake-On-Lan working per [http://askubuntu.com/questions/764158/how-to-enable-wake-on-lan-wol-in-ubuntu-16-04]("http://askubuntu.com/questions/764158/how-to-enable-wake-on-lan-wol-in-ubuntu-16-04"), but I seem to be missing one of the key files "/etc/default/tlp".

Can't find much information on why that would be.  Thoughts?

---

### Post by chili555 on 2016-11-16
Is tlp installed on your system?```
sudo dpkg -s tlp
```Perhaps try:```
sudo apt-get install tlp
```

---

