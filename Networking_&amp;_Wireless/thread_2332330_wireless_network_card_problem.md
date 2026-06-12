---
title: "wireless network card problem"
date: 2016-07-30
forum: Networking &amp; Wireless
---

### Post by aziz4212 on 2016-07-30
hi guys i have wanna change my wirelss network care to monitor mode 
but when i type ```
sudo iwconfig wlan0  mode monitor
``` thats what i got 
```
Error for wireless request "Set Mode" (8B06) :    SET failed on device wlan0 ; No such device.



```


when i type ```
ifconfig
``` that is the resulat  below
```
enp7s0    Link encap:Ethernet  HWaddr 20:47:47:00:79:6e            UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enx001e101f0000 Link encap:Ethernet  HWaddr 00:1e:10:1f:00:00  
          inet addr:192.168.8.100  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:10ff:fe1f:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21947 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25984015 (25.9 MB)  TX bytes:2665614 (2.6 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:447777 (447.7 KB)  TX bytes:447777 (447.7 KB)



```



the result of ```
lshw -c network
``` is :
```
WARNING: you should run this program as super-user.  *-network DISABLED      
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlp6s0
       version: 01
       serial: ac:d1:b8:c7:b2:ef
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:18 memory:f7200000-f7207fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 07
       serial: 20:47:47:00:79:6e
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 ioport:e000(size=256) memory:f7100000-f7100fff memory:f2100000-f2103fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: enx001e101f0000
       serial: 00:1e:10:1f:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=192.168.8.100 link=yes multicast=yes
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.



```

plz help me guys and sorry for my bad language i don't speak english very well

---

### Post by Keith_Helms on 2016-07-30
The newer releases of Ubuntu don't use wlan0 any more.  Typically an internal wifi card will have a name like wlp3s0 which I *believe* reflects it's location on the pci bus.

It looks like you're using an external USB wifi adapter.  Try using enx001e101f0000 in the command
```
sudo iwconfig enx001e101f0000 mode monitor
```

---

### Post by wildmanne39 on 2016-07-31
Hello this is not a supported topic on the forum so I closed your thread! While there are legitimate reasons to use monitor mode there is also a great risk of abuse and not everyone that reads this post would use the knowledge for good intentions.

You should try the aircrack or kali forum.
> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.
[https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

---

