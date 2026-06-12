---
title: "how to set wifi password in ubuntu-19.10-preinstalled-server-arm64+raspi3.img.xz"
date: 2019-11-10
forum: Networking &amp; Wireless
---

### Post by chelmite2 on 2019-11-10
I installed ubuntu-19.10-preinstalled-server-arm64+raspi3.img.xz on an SD card, and got my Raspberry Pi 4 to boot.
However, the next instructions in [https://ubuntu.com/download/iot/raspberry-pi](https://ubuntu.com/download/iot/raspberry-pi) say to run apt-get. Apt-get requires a network.

So, where do I add my wifi passwords? I tried putting the NetworkManager directory on a USB stick, but the Pi won't mount it.

---

### Post by uRock on 2019-11-10
Moved to ***Networking & Wireless***.

---

### Post by chili555 on 2019-11-10
> **chelmite2 said:**
> I installed ubuntu-19.10-preinstalled-server-arm64+raspi3.img.xz on an SD card, and got my Raspberry Pi 4 to boot.
However, the next instructions in [https://ubuntu.com/download/iot/raspberry-pi](https://ubuntu.com/download/iot/raspberry-pi) say to run apt-get. Apt-get requires a network.

So, where do I add my wifi passwords? I tried putting the NetworkManager directory on a USB stick, but the Pi won't mount it.You put the details in netplan. You can find a template for wireless here: 

```
cat  /usr/share/doc/netplan/examples/wireless.yaml

```Follow any changes to the /etc/netplan/*.yaml file with:

```
sudo netplan generate
sudo netplan apply
```If you need step-by-step guidance, please post back.

---

