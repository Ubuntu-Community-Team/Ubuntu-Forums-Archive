---
title: "No wireless connections"
date: 2017-08-15
forum: Networking &amp; Wireless
---

### Post by deetz2 on 2017-08-15
Hi, I installed Ubuntu onto an external drive, but I can't view any wireless connections.

```

lo        no wireless extensions.

enp8s0    no wireless extensions.

enp0s20u3c4i2  no wireless extensions.
```

In Additional Drivers, I'm using Broadcom 802.11 Linux STA wireless driver and it says it's in use. That was installed when I first installed Ubuntu. When I go to Network, I get two options for Wired (One is my phone's hotspot) and Network Proxy. When I click on the plus below, the only interface option I have is VPN. So how can I add wireless?

[My computer's specs]("https://www.cnet.com/products/toshiba-satellite-c55-c5379-15-6-core-i3-5005u-8-gb-ram-500-gb-hdd/specs/")

---

### Post by Hadaka on 2017-08-15
Hi, from a Working wired connection please do..
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
```
Then do...
```
sudo modprobe -rf wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get autoclean
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
remove wired connetion boot and test wireless
*If you have NO internet access..please let us know.
Thanks.

---

### Post by deetz2 on 2017-08-15
Thanks for your reply. I did the steps and found out Secure Boot was blocking the drivers, so I finished up the steps and disabled it. Now I can see Wifi networks, but my home router's dignal seems very weak (To be clear, Windows 10 on this same computer works well wireless). I was prompted for my password, but all I get is "(3) Device not found". Also, ifconfig doesn't seem to display anything about wireless:
```

enp0s20u1c4i2 Link encap:Ethernet  HWaddr ae:fd:ec:2d:b4:4d  
          inet addr:172.20.10.13  Bcast:172.20.10.15  Mask:255.255.255.240
          inet6 addr: 2607:fb90:6032:bc20:305d:e827:d314:ddd5/64 Scope:Global
          inet6 addr: 2607:fb90:6032:bc20:2da:aaff:bfcd:47a6/64 Scope:Global
          inet6 addr: fe80::7f07:d084:29f:3fc3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4796 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5819941 (5.8 MB)  TX bytes:613573 (613.5 KB)

enp8s0    Link encap:Ethernet  HWaddr 2c:60:0c:a9:cd:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4776 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:376230 (376.2 KB)  TX bytes:376230 (376.2 KB)

```

---

### Post by Hadaka on 2017-08-16
Hi, please use this guide and post a wireless report.
Please use a wired connection to the router if possible.
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
~OR~
Open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the wireless-info.txt
Thanks.

---

