---
title: "wifi keeps disconnecting"
date: 2015-03-02
forum: Networking &amp; Wireless
---

### Post by RAJESH_DHARMADHIKA on 2015-03-02
i have lenovo laptop which has intel wifi driver. it get's diconnected very frequently.
searched on forums for answers and tried multiple solutions but it did not solved.
based on post by Varun -
run 'wireless_script' (experimental version)  and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)
attaching output of the script.[ATTACH]260404[/ATTACH][ATTACH]260404[/ATTACH]
please help.

---

### Post by Hadaka on 2015-03-03
hi, please do..
```
sudo modprobe -rf b43
```
```
echo  "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
also change your router from TKIP  to wpa2

---

