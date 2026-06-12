---
title: "my wi-fi keeps on disconnecting"
date: 2017-03-12
forum: Networking &amp; Wireless
---

### Post by aliole4731 on 2017-03-12
I recently updated my software.now it keeps on disconnecting.although it works perfectly fine for other devices.A lot of people have the same problem but maybe this problem is sytem specific

---

### Post by jeremy31 on 2017-03-12
Please see the wireless script link in my signature and post results

---

### Post by aliole4731 on 2017-03-12
[http://paste.ubuntu.com/24165257/](http://paste.ubuntu.com/24165257/)

---

### Post by jeremy31 on 2017-03-14
Can you change the encryption settings on the access point to WPA2-PSK, WPA2-AES, or WPA2 only without WEP or TKIP

And we will disable power management on the wireless with
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by aliole4731 on 2017-03-14
can't change the encryption setting on my college wifi and disabled power management.Problem still persist.Now it shows two wifi networks with the same name(eg. my wifi name is zeh.it shows two wifi-zeh and zeh1).It connects to none properly.Please help

---

### Post by jeremy31 on 2017-03-14
If you can't change the wifi, let's try praseodym's idea from another post
```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```

---

### Post by aliole4731 on 2017-03-14
it says failed to restart wicd.service:Unit wicd.service not found
And now i have lost my network manager too.

---

### Post by jeremy31 on 2017-03-14
Just do a reboot and see if wicd shows up

---

### Post by aliole4731 on 2017-03-14
Nope.I even searched dash -no wcid.

---

