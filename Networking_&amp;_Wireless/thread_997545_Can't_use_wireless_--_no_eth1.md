---
title: "Can't use wireless -- no eth1 ??"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by jerrynewt on 2008-11-29
I have a Toshiba Satellite L305D-Amd Turion-3 Gig Ram-250 Gig HD with 8.10 and vista dual boot. In terminal "ifconfig" produces etho, lo, and pan0 --no eth1. "Sudo ifconfig eth1 up" returns "Error while getting interface flags: No such device. I have updated the driver and it is enabled in Hardware Drivers, but wicd shows no available networks. My other laptop (Satellite Pro 6100) connects just fine. I installed 8.10 on both of them with the same installation cd. Any ideas ? Thanks for the help.

---

### Post by Fir3chi3f on 2008-11-30
I assume that this is a laptop, it only has one ethernet port?

that isn't etho its eth0 (zero)

all computers start there counting from 0 not 1

that eth0 should be your wired adaptor


Do you know what kind of wireless card it is? Some wireless cards aren't automatically detected
Edit: Your wireless adapter would be recognized as wlan0

---

