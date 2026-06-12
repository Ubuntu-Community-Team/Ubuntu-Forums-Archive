---
title: "wifi doesn't work on ubuntu 18.04.01"
date: 2019-04-11
forum: Networking &amp; Wireless
---

### Post by epicfail89 on 2019-04-11
i can't connect with this pc with ubuntu... it doesn't work even in live USB... obviously with windows the wifi works perfectly

---

### Post by kc1di on 2019-04-11
Hi epicfail89 and Welcome to Ubuntu forums.

Go to a terminal and enter the following code one line at a time just copy and paste them in. Then reboot and it should work.
```
sudo apt remove bcmwl-kernel-source && sudo apt install git dkms git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```

---

### Post by oldos2er on 2019-04-11
Thread moved to *Networking & Wireless*

---

