---
title: "Cable LAN internet not working"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by onimushablade on 2008-06-12
Hello. Im new to Linux OS. I am having trouble connecting my PC to my cable modem. Im using a Phenom motherboard to lan to the modem. Ubuntu recognises my lan but wont connect. Is there a command i can use to make it connect. I tried the networking to auto with DCHP and the other one. I even tried free roaming. It wont connect. I really like ubuntu and dont want to go back to windows over no internet.

---

### Post by superprash2003 on 2008-06-13
i think you need to configure your connection to dial.. go to the terminal and type sudo pppoeconf and proceed

---

### Post by onimushablade on 2008-06-13
my modem doesnt dial to connect. im using icn a japanese company. it is really fast on this windows pc but i tried all settings.

---

### Post by chili555 on 2008-06-13
Open a terminal and please post the results of these commands:```
sudo dhclient eth0
sudo lshw -C network
ifconfig
```Thanks.

---

