---
title: "Can connect to wifi but can't use internet; Ubuntu 16"
date: 2017-11-04
forum: Networking &amp; Wireless
---

### Post by gquispemartel on 2017-11-04
So i had this problem for some days now. I get full bars on my wifi connection but can't browse internet. I've tried to solutions I could understand that I found on the forum but to no avail. Most solutions I've found  were based on the results of some input commands, Iwhich were not exactly the same as mine (iwconfig,ifconfig). I followed the "Before posting in Networking & Wireless" guide if it helps. I tried uploading wireless-info.txt but seems like it is too big to upload to the forum. If it is needed i can just copy paste it ?

I received this link that is supossed to redirect to the mentioned file:
[http://paste.ubuntu.com/25888592/](http://paste.ubuntu.com/25888592/)

Sorry if my english isn't the best it is not my primary language. Thanks in advance !

---

### Post by jeremy31 on 2017-11-04
Can you change the wifi router to channel 9 and set encryption to WPA2-AES
And ```
sudo rm /etc/modprobe.d/ath9k.conf
```

---

