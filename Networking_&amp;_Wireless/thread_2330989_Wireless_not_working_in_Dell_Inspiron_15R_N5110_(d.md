---
title: "Wireless not working in Dell Inspiron 15R N5110 (diagnostic details attached)"
date: 2016-07-17
forum: Networking &amp; Wireless
---

### Post by sudshekhar on 2016-07-17
[ATTACH]270138[/ATTACH]

I have a dell inspiron 15R and was running Ubuntu 14.04 on it without any issues. Recently, I tried xubuntu desktop by removing unity, however post that my system's wireless doesn't seem to work/is unpredictable. I've attached the output of the wireless info script above.
I tried disabling 802.11n and swcrypto params in iwlwifi but it didn't seem to work.

Pastebin link for the wireless-info :[http://pastebin.com/XztPP5ff](http://pastebin.com/XztPP5ff)

---

### Post by jeremy31 on 2016-07-17
Try disabling power management/TLP and see if you have better results.  The wireless appears to work but can't find any access points when scanning, so you could also try moving the laptop closer to the wireless router

---

### Post by Hadaka on 2016-07-17
Hi, your country code is currently showing unset, this can also be 
a factor in not connecting or drop offs, Please COPY and past one
line at  time to correct.
```
sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```
thanks.

---

### Post by sudshekhar on 2016-07-18
Hi,

I set the country code but nothing changes. This is a log report when the iwlist scan showed my wifi but it didn't connect. Also, the wifi wasn't visible from the desktop dropdown, only the terminal showed it.

[http://pastebin.com/mVMEQztX](http://pastebin.com/mVMEQztX)

Thanks for having a look!

---

### Post by jeremy31 on 2016-07-18
The wireless signals are pretty weak and WEP/TKIP encryption causes issues for most linux users.  If you can change encryption on the routers to WPA2-AES, WPA2-PSK, or WPA2 only with a 20MHz channel width it may help

---

