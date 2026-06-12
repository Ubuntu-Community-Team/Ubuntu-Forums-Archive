---
title: "Ubuntu 6.10 and HP DV6184ea with intel wireless"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by jonl on 2007-05-28
I don't get my wireless card to work with ubuntu 6.10 edgy eft. Can someone please point me in the right direction to get this to work, please :)

Sincerely
Jon

---

### Post by chili555 on 2007-05-28
If you have installed *linux-restricted-modules* which you can get through Synaptic, it should be as simple as:```
sudo modprobe ipw3945
sudo iwconfig eth1 essid <your_essid>
sudo dhclient eth1
```

This assumes you have no encryption. If you use WEP, add:```
sudo iwconfig eth1 key <your_WEP_key>
```before you dhclient.

If your encryption is WPA, please see here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by chili555 on 2007-06-09
You can find the ESSID by doing:```
sudo iwlist eth1 scan
```It may take a few tries, but you can then see the ESSID of the access point you want to connect to. Here is an example:```
 Cell 03 - Address: 00:0C:41:78:F1:93
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=40/100  Signal level=-85 dBm  Noise level=-85 dBm
                    Extra: Last beacon: 212ms ago
```That's my neighbor!

So the command would then be:```
sudo modprobe ipw3945
sudo iwconfig eth1 essid linksys
sudo dhclient eth1
```

---

