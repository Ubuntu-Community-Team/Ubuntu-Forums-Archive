---
title: "TP-Link WDN4800 disconnects and then asks for password"
date: 2016-10-01
forum: Networking &amp; Wireless
---

### Post by thenubsauce on 2016-10-01
I just got the TP-Link WDN4800. It will connect to the my xfinity moden/router, but it immediately disconnects and then asks for the password. I have searched the forums, and the post all very old. I have attached the wireless-info.txt.tar.gz file

Here's what I've tried but they haven't worked:
```
sudo apt-get install firmware-atheros
sudo modprobe -r ath9k
sudo modprobe ath9k
```

```
sudo modprobe -r ath9k
sudo modprobe ath9k
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
options ath9k nohwcrypt=1
sudo modprobe -rfv ath9k
```

Any help is appreciated, thanks

---

