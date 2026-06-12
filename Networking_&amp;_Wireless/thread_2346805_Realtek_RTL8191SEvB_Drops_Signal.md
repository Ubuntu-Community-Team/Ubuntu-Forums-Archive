---
title: "Realtek RTL8191SEvB Drops Signal"
date: 2016-12-18
forum: Networking &amp; Wireless
---

### Post by puppetjazz on 2016-12-18
Wireless drops randomly and takes a reboot to get a signal back. Fresh  install of Ubuntu MATE 16.04. Thank you for any replies, I can't find  any similiar posts. I have included the tar.gz with information

---

### Post by wildmanne39 on 2016-12-18
Please do:
```
echo "options rtl8192se swenc=1 ips=0" | sudo tee /etc/modprobe.d/rtl8192se.conf
sudo modprobe -rfv rtl8192se
sudo modprobe -v rtl8192se

```
does that help?

---

### Post by puppetjazz on 2016-12-18
I just ran the commands. I will post back if my connection drops again. Thank you for your effort.

---

### Post by puppetjazz on 2016-12-19
Seems to have helped. I only lost connection once today. That is a huge improvement. I am going to close as solved, since this solution did help significantly.

---

### Post by wildmanne39 on 2016-12-19
There is three more things that would probably help.

1. Change IEEE 802.11bgn to IEEE 802.11bg in the router.

2. Take the all special characters and spaces out of your network name.

3. Change encryption to Wpa2 AES only no TKIP.

When it disconnects try the following command to restart the network.
```
sudo  systemctl restart NetworkManager.service
```

---

