---
title: "wireless not detected in linux but works fine in windows 10"
date: 2019-05-27
forum: Networking &amp; Wireless
---

### Post by jwonch on 2019-05-27
I want to use Ubuntu instead of windows but Ubuntu doesn't detect my wireless card. I'm attaching wireless-info.txt. My computer is an hp pavilion 590.

---

### Post by jeremy31 on 2019-05-27
Boot the ISO, don't use virtualbox and post script results.

---

### Post by jwonch on 2019-05-28
So I've install the iso as a dual boot. I've included the wireless info file

---

### Post by praseodym on 2019-05-28
Driver installation via cable connection

```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh 
```
Deactivate SecureBoot before installing

---

