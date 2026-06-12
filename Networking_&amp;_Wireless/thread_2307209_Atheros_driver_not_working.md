---
title: "Atheros driver not working"
date: 2015-12-22
forum: Networking &amp; Wireless
---

### Post by stuart221 on 2015-12-22
Hi I'm unable get the wifi to work with my acer aspire E5-522-45CB wifi  Qualcomm atheros QCA9377  Ubuntu 15.10 [ATTACH]266318[/ATTACH]

---

### Post by Vladlenin5000 on 2015-12-22
Have you tried this already? -> [http://ubuntuforums.org/showthread.php?t=2304154&p=13397448#post13397448](http://ubuntuforums.org/showthread.php?t=2304154&p=13397448#post13397448)

It seems you posted there by mistake but anyway it looks like the same issue.

---

### Post by Hadaka on 2015-12-22
Hi, please copy and paste..
```
sudo iw reg set AU
sudo sed -i 's/^REG.*=$/&AU/' /etc/default/crda
sudo modprobe ath10k
```
thanks.

---

### Post by jeremy31 on 2015-12-23
See [http://ubuntuforums.org/showthread.php?t=2304250&p=13396650#post13396650](http://ubuntuforums.org/showthread.php?t=2304250&p=13396650#post13396650) to install backports and firmware can be installed by
```
git clone https://github.com/kvalo/ath10k-firmware.git
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
sudo mv /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
```

---

### Post by stuart221 on 2015-12-27
I followed [http://ubuntuforums.org/showthread.php?t=2304250&p=13396650#post13396650](http://ubuntuforums.org/showthread.php?t=2304250&p=13396650#post13396650) all fixed

---

