---
title: "Wireless connection on Asus T100HA"
date: 2018-01-23
forum: Networking &amp; Wireless
---

### Post by Br0wser on 2018-01-23
Hi all,

I am trying to get the wireless connection on an Asus T100HA laptop. I have run a script to get useful data related to the wireless, which I have attached here.

Any ideas?

Many Thanks

---

### Post by chili555 on 2018-01-23
Please get a temporary working interenet connection by ethernet, tethered or whatever means possible, open a terminal and do:```
cd /lib/firmware/brcm
sudo wget https://github.com/Asus-T100/firmware/raw/master/brcm/brcmfmac43340-sdio.txt
sudo wget https://github.com/Asus-T100/firmware/raw/master/brcm/brcmfmac43340-sdio.bin
```Reboot and tell us if the wireless is now working.

If not, please run and post:```
dmesg | grep brcm
```

---

### Post by Br0wser on 2018-01-24
Great! It worked! Thank you very much!

---

### Post by chili555 on 2018-01-24
Excellent! Glad to know it's working as expected.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

