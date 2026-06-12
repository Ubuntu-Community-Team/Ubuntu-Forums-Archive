---
title: "[Ubuntu 13.10] Strange wifi behavior."
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by pierre8 on 2014-02-16
Hi,

I installed Ubuntu 13.10 two days ago.

I have an issue with my wifi connection. I can log to my phones network wich need a password but it doesn't work with an other open network called Wifirst. I can see the network, I can try to connect but after a minute a message shows 'disconnected'.

I can't change anything into wifirst rooter because it's a residential internet provider.

My computer is an Asus RV500 and the wireless card is the intel centrino N 2230, wich is supported by firmware-iwlwifi.

When I use ifconfig, I get this when I am connected to the working network
```
wlan0     Link encap:Ethernet  HWaddr 68:5d:43:9f:ef:5c  
          inet addr:192.168.43.190  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::6a5d:43ff:fe9f:ef5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1996 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1075179 (1.0 MB)  TX bytes:329270 (329.2 KB)


```
I have the following message when I run lshw -C network.
```
 *-network               
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: 68:5d:43:9f:ef:5c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.12.0-031200-generic firmware=18.168.6.1 ip=192.168.43.190 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:46 memory:f7900000-f7901fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:04:00.2
       logical name: eth0
       version: 0a
       serial: 30:85:a9:1e:23:6f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:d000(size=256) memory:ea104000-ea104fff memory:ea100000-ea103fff


```


I made some research and I found that this strange problem often happened. So I tried what seemed to solve the problem of others like updating the kernel. But this didn't work and I have the 3.12.0-031200-generic x86_64 kernel.

Thank you for reading, I bet you can help me with this issue. I am a new linux user so I don't have a lot of knowledge.

---

### Post by varunendra on 2014-02-16
Welcome to the forums pierre8 !

I was hesitating to post because of this -
> **pierre8 said:**
> I **bet** you can help me with this issue. I am a new linux user so I don't have a lot of knowledge.
I would never bet on my knowledge. :P

But now that the post is 9 hours old and no one else has posted, let's start with whatever I can offer. It that didn't help, I have a very good knowledge about 'How To Cry for Help'. ;)

For now, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

