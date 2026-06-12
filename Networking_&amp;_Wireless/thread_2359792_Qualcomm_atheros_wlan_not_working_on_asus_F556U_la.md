---
title: "Qualcomm atheros wlan not working on asus F556U laptop"
date: 2017-04-27
forum: Networking &amp; Wireless
---

### Post by tahmid140 on 2017-04-27
I recently got the asus F556U model laptop. It comes with windows and I dual booted ubuntu 14.04 LTS. Everything works fine except the wireless lan. 

Basically the laptop boots with physical airplane mode enabled. When i go to network settings i see that airplane mode is actually **OFF**

So when i turn the **airplane mode** **on**, the physical airplane mode **light on the laptop goes off**. and vice versa.

I have run the command 'rfkill list all' and it says everything is **unblocked**. both hard and soft.

also tried the asus_nb_wmi = 4 solution floating around online. Did not work.

Please give me some suggestions. Need urgent help. TIA.

---

### Post by wildmanne39 on 2017-04-27
Click on the wireless script in my signature and follow the directions for running it and posting the link created to pastebin here.

---

### Post by tahmid140 on 2017-04-28
Here is the link of the diagnostic results, update and dist-upgrade did not solve the problem

[http://paste.ubuntu.com/24473173/](http://paste.ubuntu.com/24473173/)

---

### Post by jeremy31 on 2017-04-28
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157.8_all.deb
```
```
sudo dpkg -i linux-firmware_1.157.8_all.deb
```
Reboot

---

### Post by tahmid140 on 2017-04-28
Thanks a lot..that fixed it! :D :D

---

