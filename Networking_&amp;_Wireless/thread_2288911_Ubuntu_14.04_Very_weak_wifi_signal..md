---
title: "Ubuntu 14.04: Very weak wifi signal."
date: 2015-07-30
forum: Networking &amp; Wireless
---

### Post by Parishrut on 2015-07-30
Hello everybody. I use an HP Pavilion ab032tx notebook and recently side-loaded Ubuntu on it using a pen drive. The Wifi signal strength on this OS is unusably low and vanishes beyond 1-2 m of my router. What could be the problem? 
I previously installed the same OS using the same pen drive on another (Sony) laptop (removing Windows) and it worked perfectly.

---

### Post by Hadaka on 2015-07-30
Hi please post the output of..
```
lspci -nnk | grep -iA2 net
iwconfig
```
you may also wish to observe realtime signal strength..#the command is ONE line...press ctrl/c to exit.
```
**watch -n 1 "awk 'NR==3 {print \"WiFi Signal Strength = \" \$3 \"00 %\"}''' /proc/net/wireless"
```**

---

### Post by Parishrut on 2015-07-31
> **Hadaka said:**
> Hi please post the output of..
```
lspci -nnk | grep -iA2 net
iwconfig
```

```
08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 0a)
    Subsystem: Hewlett-Packard Company Device [103c:8096]
    Kernel driver in use: r8169


```
Thanks.

---

### Post by Hadaka on 2015-07-31
hi, please post the output of..
```
iwconfig
```
also
thakns.

---

### Post by Parishrut on 2015-08-03
```
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"vandna"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: C4:12:F5:05:A5:29   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:19   Missed beacon:0

lo        no wireless extensions.



```


Thanks. 
And thanks for the thanks.

---

### Post by Hadaka on 2015-08-03
ok, lets try this..please follow this link 
read the instructions and post the info.text file
[http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
thanks

---

