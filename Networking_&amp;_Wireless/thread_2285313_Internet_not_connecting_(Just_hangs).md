---
title: "Internet not connecting (Just hangs)"
date: 2015-07-04
forum: Networking &amp; Wireless
---

### Post by James_Ryan_Stortz on 2015-07-04
*post deleted by author.*

---

### Post by praseodym on 2015-07-05
Please run the wireless-script from the sticky thread and show the outputs.

---

### Post by James_Ryan_Stortz on 2015-07-05
*post deleted by author.*

---

### Post by praseodym on 2015-07-05
First: You need nameservers in your /etc/resolv.conf:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
```

Second:

Add the mtu value of your ISP (mostly 1500) as number instead of "Automatic" in the network-manager profile. Now try to re-connect. If it is not enough then deactivate the hardware encryption of the driver
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by James_Ryan_Stortz on 2015-07-05
*post deleted by author.*

---

### Post by James_Ryan_Stortz on 2015-07-06
*post deleted by author.*

---

### Post by James_Ryan_Stortz on 2015-07-06
*post deleted by author.*

---

