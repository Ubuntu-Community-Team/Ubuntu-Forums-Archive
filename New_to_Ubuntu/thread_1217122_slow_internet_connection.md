---
title: "slow internet connection"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by kree8or on 2009-07-19
Hi, I've just installed the latest version of ubuntu and I'm suffering slow internet connection. Its so slow, i cant watch youtube videos. I'm on a 20mb connection and other computers on the network (windows machines) get full speed. Any ideas? Thanks for your help.

---

### Post by northern lights on 2009-07-19
Please post the output of```
sudo lshw -C network
```Wireless or wired?

---

### Post by lovinglinux on 2009-07-19
See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

### Post by kree8or on 2009-07-19
> **northern lights said:**
> Please post the output of```
sudo lshw -C network
```Wireless or wired?

*-network:0             
       description: Ethernet interface
       product: 82541GI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:0a:e4:2c:40:13
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
  *-network:1
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wmaster0
       version: 01
       serial: 00:05:4e:4e:16:a3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wmaster1
       version: 01
       serial: 00:0f:ea:5c:21:9e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.0.4 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:4d:3c:84:1c:d3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

wireless

---

### Post by kree8or on 2009-07-19
Solved the problem,it was my pcmia wirelss card which was causing the problem. I pulled the card and used theone built into my thinkpad and et volia, full speed internet access.

---

