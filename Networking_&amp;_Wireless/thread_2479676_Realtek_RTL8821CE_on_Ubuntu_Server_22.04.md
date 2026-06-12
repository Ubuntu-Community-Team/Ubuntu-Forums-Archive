---
title: "Realtek RTL8821CE on Ubuntu Server 22.04"
date: 2022-10-02
forum: Networking &amp; Wireless
---

### Post by soulofoz on 2022-10-02
Problem is that the server does not associate with a  wifi network. There's a lot of discussion about this interface - I've followed the advice and updated the driver as per the tomaspinho GitHub procedure. But it wont connect to either 2.4 or 5 GHz wifi. Here is some info:

lshw output: 

```

*-network     description: Wireless interface
       product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 00
       serial: d0:a4:6f:96:9c:85
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ce driverversion=5.15.0-48-generic latency=0 multicast=yes wireless=unassociated


ip a output: 

wlp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether d0:a4:6f:96:9c:85 brd ff:ff:ff:ff:ff:ff

ifconfig output:

wlp3s0    unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry Off   RTS thr off   Fragment thr off
          Power Management off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
The wifi is up and can be seen via iwlist.

---

