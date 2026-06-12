---
title: "Ubuntu 18.04 No Wi-Fi Adapter Found Lenovo y720"
date: 2018-06-11
forum: Networking &amp; Wireless
---

### Post by tomasyhy on 2018-06-11
I have a problem with Wi-Fi connection on Ubuntu 18.04 and Lenovo Y720 with Qualcomm Atheros QCA9377. In Wi-Fi settings, I see notification: 'No Wi-Fi Adapter Found'.
Wireless info: [http://paste.ubuntu.com/p/KVjVhpQZBV/](http://paste.ubuntu.com/p/KVjVhpQZBV/)

---

### Post by jeremy31 on 2018-06-11
```
sudo apt remove bcmwl-kernel-source && echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/ideapad.conf
```
Then reboot

---

### Post by tomasyhy on 2018-06-12
Thanks a lot, works great :)

---

