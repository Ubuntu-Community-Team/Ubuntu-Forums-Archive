---
title: "Wifi occasionally auto-disconnects, can't find network on Ubuntu 18.04"
date: 2018-06-26
forum: Networking &amp; Wireless
---

### Post by jai26494 on 2018-06-26
Hey! :)

I'm relatively new to Ubuntu. I bought this computer (a Dell Inspiron 15 3565) about two months ago and it seemed buggy right on booting--the display seemed "scratchy". The right mouse button would not work on clicking the touchpad, and Netflix played a buggily too. A friend suggested a fresh install of Ubuntu and I installed Ubuntu 18.04 (it had come preinstalled with 16.04), and all but the scratchy display and the wifi issue are gone. 

For instance, while I'm using the internet, the wifi connection disconnects and the computer is no longer able to find the network. The wifi connection is being detected and working fine on other systems. On contacting Dell, I found out that the BIOS was outdated and updated it to the latest version. I can't find any driver downloads for Ubuntu 18.04 on Dell Inspiron 15 3565, if that'd help somehow. 

Please help, I don't want to move to Windows! Thanks in advance! :)

---

### Post by kc1di on 2018-06-26
Please install inxi with this command ```
sudo apt install inxi
```
once it is installed please run this command and post the output here:
```
inxi -Nn
```

---

### Post by howefield on 2018-06-26
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by jai26494 on 2018-06-26
> **kc1di said:**
> Please install inxi with this command ```
sudo apt install inxi
```
once it is installed please run this command and post the output here:
```
inxi -Nn
```

Hey! Thanks. This is what it says. 

> Network: Card-1: Realtek RTL8101/2/6E PCIE Fast/Gigabit Ethernet controller
driver: r8169
IF: enp20s0 state: down mac: 58:8a:5a:01:2d:97
Card-2: Intel Wireless 3165 driver: iwlwifi
IF: wlp22s0 state: up mac: f8:34:41:c6:3d:6a




---

