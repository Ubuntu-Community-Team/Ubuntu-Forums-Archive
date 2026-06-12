---
title: "wifi unstable with Qualcom Atheros AR9462 after upgrading 20.4"
date: 2020-05-11
forum: Networking &amp; Wireless
---

### Post by linhlc on 2020-05-11
I have just upgraded to 20.4 from 19.10.
After that wifi connection is very unstable.  I had to disconnect and connect again to the network to fix this issue.
Here is the wifi connection information.
Any idea to solve my problem?
[https://termbin.com/aj29](https://termbin.com/aj29)

---

### Post by praseodym on 2020-05-14
Lets try

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
You can also use LinSSID to search for free channels:
```

sudo apt-get install linssid
```
It looks pretty crowded.

---

### Post by linhlc on 2020-05-17
Thank you very much.
But It wasn't work for me.

---

### Post by praseodym on 2020-05-18
Ok, lets try

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by linhlc on 2020-06-04
I don't know why but after resetting modem it worked for me.

---

