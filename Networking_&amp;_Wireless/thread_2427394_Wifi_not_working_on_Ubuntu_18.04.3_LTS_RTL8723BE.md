---
title: "Wifi not working on Ubuntu 18.04.3 LTS RTL8723BE"
date: 2019-09-21
forum: Networking &amp; Wireless
---

### Post by rucafer on 2019-09-21
Hello
I have recently installed Ubuntu on my HP laptop but wifi isn't working. My network card is a RTL8723BE.
I have seen many issues with that card (related to weak signal), and I have tried all the solution given to that issues but none of them worked (maybe because my problem isn't weak signal, I don't have wifi at all!)
Thanks!

Edit:
This is the result of the script given on the sticky topic:
 [https://pastebin.com/bUvCmHmy](https://pastebin.com/bUvCmHmy)

---

### Post by mörgæs on 2019-09-23
Hi, welcome to the fora.

A good beginning would be to ask a moderator to move your thread to the networking forum. After that please read the sticky notes there - chances are that they will put you or someone else on the right track.

---

### Post by jeremy31 on 2019-09-23
Moved to Networking

---

### Post by rucafer on 2019-09-24
Thanks for the info, I have run the script suggested in one of the sticky topics and added it to the main post. And sorry for posting in the wrong forum.

---

### Post by jeremy31 on 2019-09-24
```
sudo apt remove bcmwl-kernel-source
sudo rm /etc/modprobe.d/rtl8723be.conf
 sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```

Reboot

---

### Post by rucafer on 2019-09-25
> **jeremy31 said:**
> ```
sudo apt remove bcmwl-kernel-source
sudo rm /etc/modprobe.d/rtl8723be.conf
 sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```

Reboot
I tried it and it didn't work, but thanks anyways

---

### Post by jeremy31 on 2019-09-25
Do ```
./wireless-info && cat wireless-info.txt | nc termbin.com 9999
```
Post URL

---

### Post by rucafer on 2019-09-25
[https://termbin.com/r67e](https://termbin.com/r67e)

---

### Post by jeremy31 on 2019-09-25
Try ```
sudo apt remove broadcom-sta-dkms
sudo dkms remove rtlwifi-new/0.6 --all
```
Reboot

---

### Post by rucafer on 2019-09-26
It didn't work:
[http://termbin.com/7n8y](http://termbin.com/7n8y)

---

### Post by jeremy31 on 2019-09-26
What does ```
dkms status
```
show?

---

### Post by rucafer on 2019-09-27
> **jeremy31 said:**
> What does ```
dkms status
```
show?
It doesn't show anything

---

### Post by jeremy31 on 2019-09-27
Try ```
cd rtlwifi_new
sudo make uninstall
```
Reboot

---

### Post by rucafer on 2019-09-27
Nothing changed:
[https://pastebin.com/dur0xV3g](https://pastebin.com/dur0xV3g)

---

