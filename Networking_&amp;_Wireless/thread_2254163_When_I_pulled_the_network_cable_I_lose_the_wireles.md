---
title: "When I pulled the network cable I lose the wireless connection"
date: 2014-11-25
forum: Networking &amp; Wireless
---

### Post by scorpionoir009 on 2014-11-25
When do I remove the cable stop online and I can not access wifi
When I lost the cable access and cable Bybee In


Is there a solution to the problem



```
root@pclinux:~# ifconfig -aeth0      Link encap:Ethernet  HWaddr d0:27:88:a5:e6:a2
          inet addr:192.168.1.40  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d227:88ff:fea5:e6a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1457 errors:0 dropped:860 overruns:0 frame:0
          TX packets:1465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:216182 (216.1 KB)  TX bytes:123912 (123.9 KB)
          Interrupt:16


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:861685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:861685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:73489679 (73.4 MB)  TX bytes:73489679 (73.4 MB)


wlan2     Link encap:Ethernet  HWaddr c8:be:19:d6:48:48
          inet addr:192.168.1.45  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::cabe:19ff:fed6:4848/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:2 overruns:0 frame:0
          TX packets:10 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2030 (2.0 KB)  TX bytes:1187 (1.1 KB)



```



```
root@pclinux:~# iwconfigwlan2     IEEE 802.11bgn  ESSID:"LesProDuSateam"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 78:54:2E:7F:73:82
          Bit Rate:150 Mb/s   Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-****-****   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.



```








```
  System information as of Tue Nov 25 17:32:09 CET 2014

  System load:  0.05               Processes:            106
  Usage of /:   0.9% of 145.30GB   Users logged in:      1
[COLOR=#ff0000]  Memory usage: 13%                IP address for eth0:  192.168.1.40[/COLOR]
[COLOR=#ff0000]  Swap usage:   0%                 IP address for wlan2: 192.168.1.45[/COLOR]


  Graph this data and manage this system at:
    https://landscape.canonical.com/


7 packages can be updated.
7 updates are security updates.


New release '14.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.




Your Hardware Enablement Stack (HWE) is supported until April 2017.


Last login: Tue Nov 25 17:28:19 2014 from 192.168.1.101



```




interfaces

```






auto wlan2
iface wlan2 inet static
 address 192.168.1.45
 netmask 255.255.255.0
 gateway 192.168.1.1
 wpa-conf managed
 wpa-ap-scan 1
 wpa-scan-ssid 1
 wpa-ssid LesProDuSateam
 wpa-key-mgmt WPA-PSK
 wpa-psk USMAUSMA



```



When do I remove the cable stop online and I can not access wifi
When I lost the cable access and cable Bybee In


Is there a solution to the problem

---

### Post by scorpionoir009 on 2014-11-25
;;;;;;;;;;;;;;;:!!!!!!!!!!!!!!  plz help

---

