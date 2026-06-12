---
title: "Ubuntu 18.04 slow wifi - tl-wn822N(EU) v5.0"
date: 2019-10-29
forum: Networking &amp; Wireless
---

### Post by shoopdas on 2019-10-29
The Wireless script -  [https://termbin.com/pupi](https://termbin.com/pupi)


Due to some circumstances had to move my PC and get a wireless card. as im a fat lazy ass, I've decided to go with a USB wifi card. Tp-link tl-wn822N. On Windows I get around 8MB/s while on ubuntu max I get is around 1.1MBs. 
Not sure what I'm missing to get it going faster, as it obviously can go faster. Any help is most welcome
if any additional info is needed, let me know

---

### Post by jeremy31 on 2019-10-29
```
sudo apt install git build-essential dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
sudo dkms add ./rtl8192eu-linux-driver
sudo dkms install rtl8192eu/1.0
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf
```

Reboot

---

### Post by shoopdas on 2019-10-29
Works amazingly now. sucks that I've been looking at some old thread  with old instructions on what drivers to install and they said the  ubuntu past kernel 4.2 was not supported and sucked balls overall. Tnx  for the link

Pushed to ubuntu 18.04.03 and kernel 5.0 and that  increased it form 1.1 to 2.4 or something like that, but these drivers  pushed it to standard ~8ish MB/s

tnx

mark if as solved f possible - seem to have lost the capability of doing so

---

### Post by hosjiu1702 on 2020-01-03
Thanks you so much.
It works

---

### Post by tayfunaliosman on 2020-01-11
Just used it and works amazing, thanks!!! How do you know this stuff?

---

