---
title: "Ethernet Wired Network - Not Showing"
date: 2019-09-16
forum: Networking &amp; Wireless
---

### Post by daniel-patrick on 2019-09-16
[COLOR=#242729][FONT=Arial]I can't see the 'Wired Connection' information when I go to Preferences > Network.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I can see Wireless, but nothing about Wired Connection, not even when I hook an Ethernet patch lead into the RJ-45 port socket. Do I need to re-install the drivers or network service again?

On the other hand, I have another laptop that Wireless doesn't work. [/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Anyone knows how this can be solved please?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Someone can perhaps give me a response on this?


1. I'm running Ubuntu version 18.04.3 LTS (64-bit).
2. Laptop models HP 250 G6 and HP 250 G7.
3. Wireless and Wired are enabled from the BIOS.


Out of the **discover** command (Laptop that doesn't have NIC showing)

[/FONT][/COLOR]```
daniel@ubuntu:~$ discover
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
Linux Foundation 3.0 root hub 
unknown unknown 
unknown unknown 
Linux Foundation 2.0 root hub
```

---

### Post by webaake on 2019-09-16
You have a Realtech NIC and here might be a solution for you:

[https://unixblogger.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://unixblogger.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/)

Good Luck!

---

### Post by TheFu on 2019-09-16
```
sudo lshw -C network
      and
ip a 

```
will show the important information about the card. Please post using 'code tags', like I have.  I have a realtek NIC on one of my machines.  
```
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: **r8169**
```
is uses the r8169 driver.  But there are other drivers, which is why more data is needed.

---

### Post by praseodym on 2019-09-16
> **webaake said:**
> You have a Realtech NIC and here might be a solution for you:

[https://unixblogger.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://unixblogger.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/)

Good Luck!

Or just run

```
sudo apt-get install r8168-dkms
```

and reboot.

---

### Post by daniel-patrick on 2019-09-17
**sudo lshw -C network**

```
daniel@ubuntu:~$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: e4:e7:49:84:04:8f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:3000(size=256) memory:b1104000-b1104fff memory:b1100000-b1103fff
  *-network
       description: Wireless interface
       product: Dual Band Wireless-AC 3168NGW [Stone Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: a0:a4:c5:9e:b1:9b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-62-generic firmware=29.1044073957.0 ip=172.23.12.22 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:131 memory:b1000000-b1001fff
daniel@ubuntu:~$
```




**ip a**

```
daniel@ubuntu:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether e4:e7:49:84:04:8f brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether a0:a4:c5:9e:b1:9b brd ff:ff:ff:ff:ff:ff
    inet 172.23.12.22/24 brd 172.23.12.255 scope global dynamic noprefixroute wlan0
       valid_lft 84494sec preferred_lft 84494sec
    inet6 fe80::3d85:8074:9742:42d1/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```

---

### Post by TheFu on 2019-09-17
Normally, you can only have one network connection active.  Disable the wifi if you want the wired to be used. The wifi is getting an IP somehow. Did you set it or is DHCP being used?

Please pick 1 connection to troubleshoot - wired or wifi.  I might be able to help with the wired connection.  I cannot help with wifi. I don't use wifi much.
Some normal troubleshooting steps:
[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)  Run through those steps and post the commands and results. Please.

It looks to me like the correct driver is being used for the wired connection.

---

