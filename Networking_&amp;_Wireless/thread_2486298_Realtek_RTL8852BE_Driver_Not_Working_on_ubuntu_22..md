---
title: "Realtek RTL8852BE Driver Not Working on ubuntu 22.04.2 LTS"
date: 2023-04-25
forum: Networking &amp; Wireless
---

### Post by esmn2 on 2023-04-25
Hello, i have installed ubuntu a few days ago with a dual boot win11/ubuntu on my laptop. I disabled safe boot, i have tried everything i could see on the internet for my drivers to work but everytime i try something i have different errors and its ending up not working... im sick of this not working out and i really need some help please. I dont really know where to start, but when i look the network status on a terminal there is a "UNCLAIMED" status next to my network controller : ```
  *-network UNCLAIMED       
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: ioport:f000(size=256) memory:fcf00000-fcffffff
  *-network
       description: Ethernet interface
       physical id: a
       bus info: usb@4:2
       logical name: enx207bd2730f5e
       serial: 20:7b:d2:73:0f:5e
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ax88179_178a driverversion=5.19.0-41-generic duplex=full ip=192.168.1.17 link=yes multicast=yes port=MII speed=1Gbit/s
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

Please help me

---

### Post by jeremy31 on 2023-04-25
Moved to Networking, please see the Wireless script link in my signature and post results

---

### Post by chili555 on 2023-04-25
Please check here: [https://askubuntu.com/questions/1434945/wifi-adaptor-not-found-realtek-rtl8852be-in-ubuntu-22-04](https://askubuntu.com/questions/1434945/wifi-adaptor-not-found-realtek-rtl8852be-in-ubuntu-22-04)

---

### Post by esmn2 on 2023-04-26
Hey, thanks it worked!! since im not really familiar with linux, i tried  to copy paste everything i could see on my terminal for the wifi to  work lmao. With yours it worked, tysm!!

---

### Post by chili555 on 2023-04-26
Awesome! Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

Please be aware of the warning in the README.md:

> When your kernel changes, then you need to do the following:
cd ~/rtw89
git pull
make clean
make
sudo make installYour kernel changes because Update Manager installs a newer kernel version and, after the requested reboot, the wireless is not working. If, at that time, you have no internet connectivity by ethernet, tethering or whatever means possible, then do:
```
cd ~/rtw89
make clean
make
sudo make install
sudo modprobertw89pci 
```Your wireless should then be working. Next, let's refresh the driver file:
```
make clean
git pull
make
sudo make install

```
You should be all set.

---

