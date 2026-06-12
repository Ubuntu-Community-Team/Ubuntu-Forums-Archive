---
title: "No network devices available - 16.04 (No wifi/no Ethernet)"
date: 2017-05-04
forum: Networking &amp; Wireless
---

### Post by ushakova on 2017-05-04
[COLOR=#111111][FONT=Ubuntu]Hello, 

I'm new to Ubuntu and I would appreciate your help. So, my wifi connection never worked, but I used wired and it worked perfectly well, and with no obvious reason it just stopped. I tried to reboot Network manager. I changed my /etc/NetworkManager/NetworkManager.conf to managed=true but still don't have any connection.
'System Settings/Network' gives me only 'Network Proxy' (neither 'Wireless' nor' Wifi' options). When going to 'NetWork Connections' I see some of 'Wifi' connections I had before and one 'Bridge' named 'docker0'. (I used to work with docker, never had any problems before).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here are some frequently asked commands I've tried:
[/FONT][/COLOR]```
ushakova@ushakova-HP-Notebook:~$ ifconfig 
docker0   Link encap:Ethernet  HWaddr 02:42:5c:b9:d1:e8  
      inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
      UP BROADCAST MULTICAST  MTU:1500  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0 
      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:65536  Metric:1
      RX packets:4972 errors:0 dropped:0 overruns:0 frame:0
      TX packets:4972 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1 
      RX bytes:373328 (373.3 KB)  TX bytes:373328 (373.3 KB)

ushakova@ushakova-HP-Notebook:~$ iwconfig 
lo        no wireless extensions.

docker0   no wireless extensions.
ushakova@ushakova-HP-Notebook:~$ vim /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

ushakova@ushakova-HP-Notebook:/etc/NetworkManager$ vim NetworkManager.conf 

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=true



ushakova@ushakova-HP-Notebook:$ lspci -knn | grep -EA2 'Eth|Net'
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:8305]
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
DeviceName:  
Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:81c1]

ushakova@ushakova-HP-Notebook:$ rfkill list all
**NO OUTPUT**

```

Thank you!

---

### Post by wildmanne39 on 2017-05-04
Give post 4 a try here, I think that will fix it but the changes you made to the network file, changing false to true you may have to change that back because the value should be false.
[https://ubuntuforums.org/showthread.php?t=2360330](https://ubuntuforums.org/showthread.php?t=2360330)

---

### Post by ushakova on 2017-05-04
It works!! So simple and elegant - thank you!

---

### Post by wildmanne39 on 2017-05-04
Your welcome!
Enjoy!:)

---

