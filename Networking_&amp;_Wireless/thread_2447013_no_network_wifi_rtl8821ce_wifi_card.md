---
title: "no network wifi rtl8821ce wifi card"
date: 2020-07-10
forum: Networking &amp; Wireless
---

### Post by kickass1955 on 2020-07-10
i just installed ubuntu 20.04 mate.have ubuntu 18.04 lts and had to build drivers for 18.04.
now i have to build again for this distro...can i use the files from 18.04 or do i  need to download from 20.04 repository
and i need to know what files.

---

### Post by kc1di on 2020-07-11
Unfortunately the driver for the RTL8821ce is not included in Ubuntu's install you will have to install it from else where. 
If you can connect to the internet via Ethernet cable you can run these commands in a terminal (one at a time) and install the needed driver.
```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh
```
then reboot and your wifi should be working.
good luck

---

### Post by kickass1955 on 2020-07-11
thank you...will try this

---

### Post by kickass1955 on 2020-07-11
that worked.....i will mark as solved...thank you

---

### Post by kc1di on 2020-07-11
Your welcome, enjoy :)

---

