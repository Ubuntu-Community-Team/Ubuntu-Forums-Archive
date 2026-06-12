---
title: "How to disable wifi power saving in Ubuntu Server 20.04.4 LTS"
date: 2022-04-10
forum: Networking &amp; Wireless
---

### Post by codrut-popescu on 2022-04-10
```
iwconfig
lo        no wireless extensions.


eno1      no wireless extensions.


wlp0s20f3  IEEE 802.11  ESSID:"Unifi"  
          Mode:Managed  Frequency:5.2 GHz  Access Point: 74:AC:B9:46:86:15   
          Bit Rate=292.5 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:156   Missed beacon:0

```
This command works:
          
sudo iwconfig wlp0s20f3 power off


```
iwconfig
lo        no wireless extensions.


eno1      no wireless extensions.


wlp0s20f3  IEEE 802.11  ESSID:"Unifi"  
          Mode:Managed  Frequency:5.2 GHz  Access Point: 74:AC:B9:46:86:15   
          Bit Rate=292.5 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:159   Missed beacon:0

```          
However at reboot it is still on.
I have found some mentions I need to edit /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf but this file does not exists on my system.


```
tree NetworkManager/
NetworkManager/
&#9492;&#9472;&#9472; dispatcher.d
    &#9492;&#9472;&#9472; hook-network-manager


1 directory, 1 file

```

---

### Post by chili555 on 2022-04-14
Network Manager is seldom installed in servers. 

The silence your question has received reflects the lack of any obvious way to do this in a server. I assume that no obvious answer exists because servers are seldom connected by wifi. However, we may find some way to so this at the driver level. Please run and post:
```
lspci -nnk | grep 0280 -A3
```Thanks.

---

