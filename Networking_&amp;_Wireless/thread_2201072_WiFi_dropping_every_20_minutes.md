---
title: "WiFi dropping every 20 minutes"
date: 2014-01-22
forum: Networking &amp; Wireless
---

### Post by ikotlyarsky on 2014-01-22
[ATTACH]249665[/ATTACH]

Running :
Ubuntu 12.04 on Lenovo T410

Please take a look at the WIFI info in the file attached.  Any suggestions will be appreciated

---

### Post by praseodym on 2014-01-22
Try to update the driver:
```

sudo apt-get install --reinstall build-essential linux-headers-$(uname -r) linux-headers-generic-pae
wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo cp -r firmware/* /lib/firmware  
```
Reboot.

---

