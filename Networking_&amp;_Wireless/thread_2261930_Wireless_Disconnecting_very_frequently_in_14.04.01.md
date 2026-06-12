---
title: "Wireless Disconnecting very frequently in 14.04.01 LTS"
date: 2015-01-22
forum: Networking &amp; Wireless
---

### Post by vijay_shyam on 2015-01-22
Hi tech geeks of linux. Ima newbie in linux. Few days before i have installed Ubuntu 14.04.01 LTS on my Lenovo G 50-30 Laptop. Everything is working fine except few which are 

1. My wireless disconnects every 5 mins. I need to restart and use " sudo modprobe -r ideapad_laptop ". This command i found somewhere searching and it helped me to coonect to wifi. Though it gets disconnected every 5 mins

2. I try to reduce brightness of the screen and it stays same. 

Sorry as im very new to linux i dont have much knowledge about linux terminal commands and scripts. Still expecting solution from this forum


Regards
Vijay

---

### Post by Pilot6 on 2015-01-22
Give output of

lspci -knn | grep Net -A2

---

### Post by vijay_shyam on 2015-01-23
out put is 

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

---

### Post by vijay_shyam on 2015-01-23
In addition to this i found another new problem with my laptop is

1. Laptop is freezing after some time once or twice a day

---

### Post by Pilot6 on 2015-01-23
[http://ubuntuforums.org/showthread.php?t=2261702](http://ubuntuforums.org/showthread.php?t=2261702)

---

### Post by vijay_shyam on 2015-01-25
Thank you Pilot6 for your time.. It helped me somehow.

Updated kernel from 3.13 to 3.18 and everything is perfectly working except at time " system is getting freeze " . I have to hard restart the system. Any solution for that problem i would be great full.

---

