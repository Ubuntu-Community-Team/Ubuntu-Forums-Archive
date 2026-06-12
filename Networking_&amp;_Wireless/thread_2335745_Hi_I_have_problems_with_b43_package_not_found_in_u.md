---
title: "Hi I have problems with b43 package not found in ubuntu 14.04"
date: 2016-08-31
forum: Networking &amp; Wireless
---

### Post by teno93 on 2016-08-31
I just installed Ubuntu Linux and am new to the OS. I have been googling how to fix the no wifi connectivity problem but haven't any luck as my problem seems to be related to the b43 package not being installed on the laptop. I have found the bcm43xx0o.fw file in lib/firmware/brcm but cant load it I don't know the commands required to do this in terminal can someone tell me what I need to do to load the files? I don't have internet access on the laptop so I cannot download the file. please help me as I am willing to stick with Linux I like the idea of being different from windows users thank you 

teno

---

### Post by jeremy31 on 2016-08-31
*Thread moved to **Networking & Wireless**.*
The first thing I would try with an internet connection is ```
sudo apt-get install firmware-b43-installer
```
Reboot

If that fails please post results for ```
lspci -nnk | grep -iA2 net
```

Welcome to ubuntuforums

---

