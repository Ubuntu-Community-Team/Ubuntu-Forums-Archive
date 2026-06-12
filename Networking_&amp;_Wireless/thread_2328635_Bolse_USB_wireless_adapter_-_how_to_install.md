---
title: "Bolse USB wireless adapter - how to install"
date: 2016-06-23
forum: Networking &amp; Wireless
---

### Post by ineuw on 2016-06-23
I am using the Bolse BO-N1566 300mbps WiFi adapter on a desktop with Xubuntu 14.04 32 bit. Below is the output for lshw. It constantly drops the connection. 

```

ineuw@xu1404:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Attansic L1 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:18:f3:9d:76:be
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:fe9c0000-fe9fffff memory:fe9a0000-fe9bffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1
       logical name: wlan1
       serial: e8:4e:06:39:ec:84
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.13.0-88-generic firmware=N/A ip=192.168.1.145 link=yes multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by howefield on 2016-06-23
Post moved to own thread.

---

### Post by kurt18947 on 2016-06-23
I don't routinely use an rtl8192cu based wifi device. I did plug one in while 16.04 was in development just before release to see if this problem had been fixed.  It hadn't.
> configuration: broadcast=yes **driver=rtl8192cu** driverversion=3.13.0-88-generic 


rtl8192cu is a known problem child. For Ubuntu 14.04 this should fix your problem:

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

I've seen reports that this fix may not work for 16.04. See post #2 in this thread for an alternative:

[http://ubuntuforums.org/showthread.php?t=2328230&highlight=8192cu](http://ubuntuforums.org/showthread.php?t=2328230&highlight=8192cu)

The following post says that didn't work. This may be why:


**rtl8xxxu **              69632  0
mac80211              659456  1 [B]rtl8xxxu


[/B]I've read some place that the included problem driver - rtl8192cu - had been replaced with rtl8xxxu. I noticed that module 
when I was checking my device. Unfortunately the newer module didn't appear to work any better than the old one, it would work for a few minutes then hang. The 'broken' module must be blacklisted  in order for the correctly functioning module to load. You can determine which broken module you have loaded with the command 'lsmod', you should have either rtl8192cu or rtl8xxxu. The broken module must be blacklisted in /etc/modprobe.d/blacklist.conf. in order for the functioning module to load.

---

### Post by ineuw on 2016-06-23
kurt18947, thanks for your kind help. The solution [http://ubuntuforums.org/showthread.php?t=2328230&highlight=8192cu](http://ubuntuforums.org/showthread.php?t=2328230&highlight=8192cu) seems to be working well so far (30 minutes). The test came with the download of the software updates. Also checked the blacklist and it is blacklisted. lwconfig results here are identical to Windows 7 results.

```

ineuw@xu1404:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"HomeWiFi"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 30:85:A9:8A:7F:20   
          Bit Rate:144.4 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=91/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by QDR06VV9 on 2016-06-23
Thanks for crediting efforts by kurt18947....And Thanks for sharing your solution.
If you would be as kind to mark your thread as solved as to help other visitors to this thread.
Thanks and kind Regards

---

