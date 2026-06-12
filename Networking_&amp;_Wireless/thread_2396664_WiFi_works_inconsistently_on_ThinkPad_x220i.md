---
title: "WiFi works inconsistently on ThinkPad x220i"
date: 2018-07-19
forum: Networking &amp; Wireless
---

### Post by timur38 on 2018-07-19
Hello,

I just installed latest Ubuntu on the old ThinkPad x220i and at the beginning WiFi didn't work at all until I ran  sudo apt-update sudo apt dist-upgrade. It worked very well shortly after commands but stopped in 5 minutes. Right now it either works very slowly under 1mbps or doesn't work at all. The wired connection works good.
I would appreciate any help.

Thanks

---

### Post by jeremy31 on 2018-07-19
See if chili555's instructions @ [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520) help any.  If they don't see the wireless script link in my signature and post results

---

### Post by timur38 on 2018-07-20
Hi Jeremy31, chili555's instructions didn't help. I added wireless-info. Thanks!

---

### Post by praseodym on 2018-07-20
Try
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi-11n.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by timur38 on 2018-07-21
> **praseodym said:**
> Try
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi-11n.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Thank you that worked.

---

