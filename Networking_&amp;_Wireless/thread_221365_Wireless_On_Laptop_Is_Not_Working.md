---
title: "Wireless On Laptop Is Not Working"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by ROADRUNNER66 on 2006-07-23
Hello, my laptop has a BROADCOM 802.11b/g WLAN and I cant seem to get onto the internet. Whenever I go to the get started link it tells me that the address cant be found, does anyone have any ideas? Thanks.

---

### Post by FizDev on 2006-07-23
Try installing your wireless card driver's using ndiswrapper.

First, install ndiswrapper
```
sudo apt-get install ndiswrapper-utils
```

Then, install the driver
```
sudo ndiswrapper -i driverfilename.inf
```

List the installed drivers...
```
sudo ndiswrapper -l
```
...if you see your driver, continue

Then
```
sudo modprobe ndiswrapper
```
and/or (i can't remember)
```
sudo ndiswrapper -m
```

---

