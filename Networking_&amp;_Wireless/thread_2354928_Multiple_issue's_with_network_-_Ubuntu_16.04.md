---
title: "Multiple issue's with network - Ubuntu 16.04"
date: 2017-03-07
forum: Networking &amp; Wireless
---

### Post by zfar on 2017-03-07
I recently installed Ubuntu for my work and as usual installed the latest version 16.04.2. but unfortunately facing a very annoying problem with network and wifi. and i did my best till now to find some work around for this as i see many have reported similar kind of issue's.

First issue i can't see and enable the wifi icon, on top right as an tray icon. 


second issue, my wireless network (setting->network->wireless) window is continuously not responding, each time i tried to connect with any other wifi, either it will not respond or just close/crashed automatically rite aftewords


Regards

---

### Post by jeremy31 on 2017-03-07
See the wireless script link in my signature and post your results

Welcome to the forums

---

### Post by zfar on 2017-03-07
[http://paste.ubuntu.com/24133780/](http://paste.ubuntu.com/24133780/)


here are the posted results

---

### Post by jeremy31 on 2017-03-08
I would try setting the country code
```

sudo iw reg set DE
```
```
sudo sed -i 's/^REG.*=$/&DE/' /etc/default/crda

```

As you had US for a country code when you appear to be in Germany trying to use channel 13 which is not allowed in the US

Check ```
dpkg -l | grep indicator-network
```
There might be a hint as why the network icon is missing

---

