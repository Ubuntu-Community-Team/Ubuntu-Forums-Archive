---
title: "Panda PAU05, Ubuntu 17.10 wifi constantly dropping"
date: 2018-01-27
forum: Networking &amp; Wireless
---

### Post by huysmans on 2018-01-27
I built a PC a few months ago and have been attempting to use a Panda USB adapter to connect to the Internet. My wifi network is often not recognized at all. On the occasions when I am able to establish a connection, the connection is very poor and unstable. Here are the results from running the wifi script: [https://pastebin.ubuntu.com/26469007/](https://pastebin.ubuntu.com/26469007/)

I'd appreciate any help you might be able to offer. Thanks in advance!

---

### Post by praseodym on 2018-01-27
Lets try
```

sudo modprobe -rfv rt2800usb
sudo modprobe -v rt2800usb nohwcrypt=1
```
If it works make it permanent
```

echo "options rt2800usb nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800usb.conf
```

---

