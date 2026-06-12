---
title: "any tips to improve connection speed with a wireless n card?"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by lime4x4 on 2008-02-11
i have a linksys 300n pci wireless card installed in gutsy using ndiswrapper.When down loading a file from the net i get around 90Kb per sec sometimes less. if i go to my other computer which is hardwired i can download the same file at around 945Kb per sec. Just thought wireless n should be faster. I have 86% signal strength and using a linksys n router

---

### Post by jan quark on 2008-02-12
please post the output of

```
iwconfig
```
```
ifconfig
```

---

### Post by lime4x4 on 2008-02-12
I also noticed that on mythtv box which uses a wireless G card can download at around 280 to 320 KB. Here is the output of the pc running the wireless N card
also here is the output of lspci

01:00.0 Network controller: Broadcom Corporation BCM43XG (rev 01)

john@pammy-desktop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"transformers"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1C:10:C7:52:26   
          Bit Rate=40.5 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

john@pammy-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5747 (5.6 KB)  TX bytes:5747 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1D:7E:9D:1E:3A  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7eff:fe9d:1e3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17482601 (16.6 MB)  TX bytes:5065166 (4.8 MB)
          Interrupt:21 Memory:feaec000-feaf0000 

john@pammy-desktop:~$

---

