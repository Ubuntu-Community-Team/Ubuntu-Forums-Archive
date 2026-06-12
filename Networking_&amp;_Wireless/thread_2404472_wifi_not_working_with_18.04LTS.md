---
title: "wifi not working with 18.04LTS"
date: 2018-10-24
forum: Networking &amp; Wireless
---

### Post by mmelgaco on 2018-10-24
hi, i was using ubuntu 16.04LTS fine, my wifi was working ok.

Yesterday i upgraded it to 18.04LTS.

Now my wifi is not working anymore.

lspci -vvnn | grep Network02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak] [8086:0091] (rev 34)

Can you help me? Thanks

---

### Post by wildmanne39 on 2018-10-24
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by mmelgaco on 2018-10-24
Here is more information: [https://paste.ubuntu.com/p/7vnZFHzZqr/](https://paste.ubuntu.com/p/7vnZFHzZqr/)

Please help me, i need my wifi working...

---

### Post by jeremy31 on 2018-10-24
Do one line at a time
```
sudo apt-get purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```

Reboot and run the wireless script again if it doesn't work

---

