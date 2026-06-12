---
title: "why Internet connection keeps dropping out"
date: 2018-01-22
forum: Networking &amp; Wireless
---

### Post by sleepingpills on 2018-01-22
Recently i was installed ubuntu 17.10 in my laptop. But I am facing internet connection problem which is automatically keeps dropping out. Please help me to resolve this issue. i attach two screenshot of [COLOR=#000000][FONT=&quot]lspci  and [/FONT][/COLOR][COLOR=#000000][FONT=&quot]sudo lshw -C network[/FONT][/COLOR]

---

### Post by wildmanne39 on 2018-01-22
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created. 

Please do not post images of code it is to small and hard to read.

Thanks

---

### Post by sleepingpills on 2018-01-23
still now don't get any solution. please check the attachment

---

### Post by wildmanne39 on 2018-01-23
I see a few things that have been changed manually, we are going to try a driver parameter and if that does not fix it go into network manager and set IPV6 to ignore and post the name of the network you want to connect too. 

Please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Does that help?

---

