---
title: "Wifi Connection Drops Out (Ubuntu 16.10 64x)"
date: 2017-01-12
forum: Networking &amp; Wireless
---

### Post by mdfoysalhossainsohag on 2017-01-12
Hi, I'm using HP Laptop. My Wireless Device is "RT3290". I've followed almost all posts in the forum but didn't worked for me.

Now I've two problem
- Wifi Connection Drops Out Frequently
- Sometimes wifi is not shown after boot

Can anyone here to help me fixing this?

Thanks.

---

### Post by dcompany on 2017-01-12
check this link [http://www.linuxlinx.com/2016/05/install-realtek-rtl8723be-wifi-driver-ubuntu-linuxmint.html](http://www.linuxlinx.com/2016/05/install-realtek-rtl8723be-wifi-driver-ubuntu-linuxmint.html). I did for my HP laptop, it seems like wifi antena value was not set properly.

---

### Post by mdfoysalhossainsohag on 2017-01-12
Sorry, It's not working for me...
I've tried manual system. Because when I follow first options (fatal error shows)..
Few things to be noted that-
When I run the following lines, wifi works for few minutes---

sudo ifconfig eno1 up


sudo service network-manager restart

---

### Post by jeremy31 on 2017-01-12
Please post results for ```
cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf; iwconfig; dmesg | grep rt2800
```

---

