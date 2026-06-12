---
title: "Ralink RT3290 slow wifi speed ubuntu 16.10"
date: 2017-04-08
forum: Networking &amp; Wireless
---

### Post by lemonsix on 2017-04-08
So i've been having some trouble since i changed from debian to ubuntu 16.04 with this wifi card, but now is worse because internet is working at 1mbps since i update to 16.10.
Way back when I had debian installed, i used Sinergy so I could get mouse and keyboard from my Desktop pc over lan, but with ubuntu this doesn't work, it's all laggy and unstable.

here's my adapters data
[https://pastebin.com/RhQadSAw](https://pastebin.com/RhQadSAw)

If any of you could help me it would be awesome

---

### Post by Hadaka on 2017-04-09
Hi, from a working wired connection please copy and paste one line at a time...
*Correcting your driver
```
sudo modprobe -rfv rt3290sta rt2860
sudo apt-get remove --purge rt3290sta
sudo modprobe -v rt2800pci
```
*Setting your country code.
AR    -    America/Argentina/Catamarca    Catamarca
```
sudo iw reg set AR
sudo sed -i 's/=.*/=AR/' /etc/default/crda
```
remove wired connection, boot and test wireless
Thanks.

---

