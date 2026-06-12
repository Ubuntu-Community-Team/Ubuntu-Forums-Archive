---
title: "Wireless networks detected but can't connect, please help"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by bojack on 2008-08-27
I can detect unsecured public wireless networks, but I can't connect to them. It says it is trying to obtain an IP address for a while, and then it just gives up and says not connected. What really pisses me off is that it works totally flawlessly in windows. It seems that loads and loads of people have been having this issue but no solutions. If no one can find a way to fix it I am afraid I will need to go back to windows, Ubuntu is pretty awesome but I can't not have internet working (the final straw in a slowly building list of complaints I have with ubuntu) 

Please help! I have tried wicd, doesn't work. Tried reinstalling, doesn't work. I am in ubuntu 8.04 by the way.

---

### Post by panhandle on 2008-08-27
Please post the results of the following command:

```
lshw -C network
```

and also:

```
ifconfig
```

---

### Post by bojack on 2008-08-27
Here

>   description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: wmaster0
       version: 00
       serial: 00:1a:ef:02:12:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g

> 
wlan0     Link encap:Ethernet  HWaddr 00:1a:ef:02:12:b4  
          inet6 addr: fe80::21a:efff:fe02:12b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37044 (36.1 KB)  TX bytes:11396 (11.1 KB)

---

### Post by panhandle on 2008-08-27
see the following link:

[http://ubuntuforums.org/showthread.php?t=314974](http://ubuntuforums.org/showthread.php?t=314974)

Other people have had issues with this chipset as well.

---

### Post by panhandle on 2008-08-27
I reread your post and mine, and I was thinking:

If so many people have had problems with this chipset (seems like you have done some research) and you are unable to find a satisfactory workaround, why not just buy a USB dongle that you know will work with Ubuntu? This way you don't have to go back to windows.

---

