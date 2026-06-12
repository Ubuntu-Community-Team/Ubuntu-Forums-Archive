---
title: "No Wireless Card found"
date: 2018-05-21
forum: Networking &amp; Wireless
---

### Post by ccouch1982 on 2018-05-21
Hi, just installed Ubuntu a couple of days ago and it can't find my wireless card.  Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 P.  Thanks

---

### Post by wildmanne39 on 2018-05-21
Hello and welcome the the forum, the device you listed is your ethernet connection,

Please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by ccouch1982 on 2018-05-21
[http://paste.ubuntu.com/p/pFXCHGc78M/](http://paste.ubuntu.com/p/pFXCHGc78M/)

---

### Post by wildmanne39 on 2018-05-21
Please do:
```
sudo apt install --reinstall linux-headers-$(uname -r) build-essential dkms git
git clone -b extended --single-branch https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms build rtlwifi-new/0.6 
sudo dkms install rtlwifi-new/0.6

```
If you notice a weak signal do:
```
sudo /bin/sh -c 'echo "options rtl8723de ant_sel=2" >> /etc/modprobe.d/rtl8723de.conf'
```
if not better then do:
```
sudo /bin/sh -c 'echo "options rtl8723de ant_sel=1" >> /etc/modprobe.d/rtl8723de.conf'
```

---

