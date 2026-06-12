---
title: "problem in installing wifi driver for Dell Vostro 1520 wifi"
date: 2021-02-10
forum: Networking &amp; Wireless
---

### Post by mdfeiza on 2021-02-10
Hello every one.
I installed a 32 bit version of ubuntu on my laptop. and I have problem with wifi.
please tell me how can I install wifi driver?

---

### Post by CelticWarrior on 2021-02-10
Welcome.

Please start by installing a current 64-bit Ubuntu or a lighter flavor such as Lubuntu or Xubuntu, given the age of the computer.
32-bit architecture is as good as dead and not required unless the hardware only supports 32-bit, not the case here.

The WiFi must work out-of-the-box.

---

### Post by slickymaster on 2021-02-10
*Thread moved to **Networking & Wireless**.*

---

### Post by mdfeiza on 2021-02-12
I installed ubuntu 20,10
then used three commands
sudo apt update
sudo apt install bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
then the problem solved.

---

