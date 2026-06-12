---
title: "ubuntu boot without full network configuration"
date: 2017-02-08
forum: Networking &amp; Wireless
---

### Post by theend66 on 2017-02-08
Hi all, 

Each time i boot up i get this message before the log in page arrives (ubuntu boot without full network configuration). 

But upon login, WICD starts up and connects to the ethernet cable by itself. If no ethernet cable is connected then ill have to manually connect to my wifi.  

But the problem i have been facing for sometime now is that if ii was to connect to the wifi instead of the ethernett cable, my wifi connection last for the most of 5mins and then the though it shows connected i am unable to surf the net. This is seriously affecting my work.

I am now wondering if the boot up error has anything to do with this? And how do i solve the booting without full network configuration issue?

```
 sudo lshw -C network
[sudo] password for themessiah: 
  *-network               
       description: Wireless interface
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 31
       serial: 94:53:30:71:8d:87
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.4.0-59-generic firmware=WLAN.TF.1.0-00267-1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:282 memory:df000000-df1fffff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 07
       serial: 18:db:f2:06:16:9f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.1.135 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:127 ioport:d000(size=256) memory:df200000-df200fff memory:d0300000-d0303fff


```

```
 ifconfig -a
eth0      Link encap:Ethernet  HWaddr 18:db:f2:06:16:9f  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1adb:f2ff:fe06:169f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9541 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11506994 (11.5 MB)  TX bytes:726261 (726.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:29661 (29.6 KB)  TX bytes:29661 (29.6 KB)

wlan0     Link encap:Ethernet  HWaddr 94:53:30:71:8d:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 94:53:30:71:8d:87  
          inet addr:169.254.7.222  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1


```

Help will be greatly appreciated :)

---

### Post by Hadaka on 2017-02-08
Hi, this may be causing your issues...
wlan0:avahi Link

please post the output of...
```
cat /etc/network/interfaces
```
Thanks

---

