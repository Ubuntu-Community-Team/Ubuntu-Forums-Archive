---
title: "Dell D530 Wifi Drivers"
date: 2020-02-19
forum: Networking &amp; Wireless
---

### Post by christianbmx on 2020-02-19
I have an old Dell D530 and I can't run the wifi. I used the lspci | grep -i network command and the results are: 0c: 00.0 Network controller: Broadcom Inc. and subsidiaries BCM4311 802.11a / b / g (rev 01

And until that point I arrive and I don't know what else to do. Can anyone help me.
I don't know what I'm missing, I don't understand why in some distributions of linux or windows I don't have this problem. I am new to ubuntu and I want to have the system installed and working to be able to practice and learn, but without Wi-Fi it doesn't help me. Sorry, I'm using a translator.

---

### Post by wildmanne39 on 2020-02-19
Hello and welcome to the forum.

Please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by christianbmx on 2020-02-20
Hi and thanks for your time. This is the link to the pastebin with the info in ubuntu. [https://pastebin.com/bKiF1Qb1](https://pastebin.com/bKiF1Qb1)

---

### Post by jeremy31 on 2020-02-20
Just do ```
sudo apt update && sudo apt install firmware-b43-installer
```
Reboot

---

### Post by christianbmx on 2020-02-20
> **jeremy31 said:**
> Just do ```
sudo apt update && sudo apt install firmware-b43-installer
```
Reboot

Ohh thanks a lottttttt. Its working. My pain its over. Thanks again. Ill save this data for the future

---

### Post by CelticWarrior on 2020-02-21
FYI, there's a [sticky thread]("https://ubuntuforums.org/showthread.php?t=2214110") for everything related to Broadcom WiFi chipsets. ;)

This is the bookmark you should save for future reference. If you need to deal with another one in the future you can refer to this thread, the driver to install may or may not be the same, it depends on the specific model.

---

