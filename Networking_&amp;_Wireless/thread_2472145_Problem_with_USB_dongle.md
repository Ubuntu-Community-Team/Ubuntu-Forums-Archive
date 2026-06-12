---
title: "Problem with USB dongle"
date: 2022-02-18
forum: Networking &amp; Wireless
---

### Post by temuko on 2022-02-18
Hi

I just installed ubuntu with the intention of staying here.

The problem is Ubuntu dont recognize my usb dongle and i dont know how to solve it. I dont have drivers but i dont know if i can get some generic drivers for it. In thin moment im connecting with the phone. 

In the terminal, with **lsusb** i get this:

**Bus 002 Device 007: ID 0bda:c811 Realtek Semiconductor Corp. **

The adapter is MAXESLA Antena WIFI USB 600Mbps.

I dont know how to do it. I saw some information but only when you have drivers for install it. 


Thanks and sorry for my english

---

### Post by SeijiSensei on 2022-02-18
First, try going to System Settings > Driver Manager and see if the application detects your device and downloads the necessary drivers.

---

### Post by chili555 on 2022-02-18
Please check here: [https://askubuntu.com/questions/1162974/wireless-usb-adapter-0bdac811-realtek-semiconductor-corp/1163018#1163018](https://askubuntu.com/questions/1162974/wireless-usb-adapter-0bdac811-realtek-semiconductor-corp/1163018#1163018)

---

### Post by temuko on 2022-02-19
Thanks dude !!! 

I really love this community , i solved it with the page.

Ty <3

---

### Post by chili555 on 2022-02-19
Awesome. I'm glad it's working as expected. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by morrownr on 2022-02-20
> **temuko said:**
> Thanks dude !!! 

I really love this community , i solved it with the page.


I understand that you have solved the issue but in case anyone in the future is looking, a much more modern version of the 8811cu driver is available at:

[https://github.com/morrownr/8821cu](https://github.com/morrownr/8821cu)

This driver was released within the last 2 weeks.

Regards

---

