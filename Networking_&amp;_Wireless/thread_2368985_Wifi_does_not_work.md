---
title: "Wifi does not work"
date: 2017-08-17
forum: Networking &amp; Wireless
---

### Post by poolq2 on 2017-08-17
Hello,

have a new lenovo v510 notebook tried 

sudo apt update
sudo apt dist-upgrade

and 

sudo apt install pastebinit

did not work.

[http://paste.ubuntu.com/25331717/](http://paste.ubuntu.com/25331717/)

please help

---

### Post by jeremy31 on 2017-08-17
```
echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/ideapad_laptop.conf
```
Reboot and it should work

---

