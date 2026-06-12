---
title: "AAARGHHH.....&gt;Belkin F5D7050"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by dean20007 on 2007-05-20
Please help....I am going insane

I am trying to install my belkin F5D7050. followed this step by step

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29))

which is excellent I might add. 

But i get nothing. Everything seems to follow the steps but when using ifup wlan0, I get a brief flicker of light from the dongle then it doesn't connect. I have ensured that the WEP key is correct. and IP address is valid(using static ip) but nothing. 

iwconfig *appears* to find my network as it finds the MAC address of the access point. 

Please help me

---

### Post by Kobalt on 2007-05-20
Are you using Ubuntu 7.04 ? or Network-manager in another version of Ubuntu ? If so, you don't need to/must not edit the /etc/network/interfaces file, Network-Manager handles this by himself. That means you need to skip this part in the HowTo, and finish by doing a ```
sudo modprobe rt73
```
If you already modified the /etc/network/interfaces file, remove anything you added and leave only the lo interface. 
You may need to restart your computer for changes to take effect.

---

