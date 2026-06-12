---
title: "Ubuntu server 18.04 no internet connection"
date: 2018-10-26
forum: Networking &amp; Wireless
---

### Post by almedina on 2018-10-26
Hi everyone, I hope somebody can help me with this issue, I did a fresh install of ubuntu server 18.04 on a specific computer, internet connection is working fine but when I transfer the hard drive on a different Motherboard it does not get any DHCP connection.

I've tried to setup a static ip address using this tutorial but it did not work, [https://askubuntu.com/questions/1029531/how-to-setup-a-static-ip-on-ubuntu-18-04-server](https://askubuntu.com/questions/1029531/how-to-setup-a-static-ip-on-ubuntu-18-04-server)

This is my setup
Ubuntu server 18.04
Xfce4 slim GUI

Thank you in advanced for any help.

---

### Post by almedina on 2018-10-27
I  just fixed the issue in the following way, from previous computer the network driver was "enp1s0" and it did not changed when moved the hard drive into another computer, so I changed from "enp1s0" to "enp2s0" and problem fixed, I'll leave the thread here if someone has a similar situacion.

---

