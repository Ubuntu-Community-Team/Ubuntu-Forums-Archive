---
title: "Wi-Fi Shows network at weak signal and doesn't connect"
date: 2016-10-06
forum: Networking &amp; Wireless
---

### Post by anuranjan on 2016-10-06
I have dual booted Ubuntu 16.04 and have problems in my wi-fi connection. First it was disabled and greyed out and I applied many solutions on this forums. Now, there is a very weak Wi-Fi signal showing up which doesn't connect.
> 
USING: iwconfig

lo        no wireless extensions.

wlo1      IEEE 802.11bgn  ESSID:"Some Wifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:68:2F:91:21   
          Bit Rate=65 Mb/s   Tx-Power=18 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:81   Missed beacon:0

eno1      no wireless extensions.

enp0s20u1  no wireless extensions.

USING: lspci -vvnn | grep Network

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]




---

### Post by howefield on 2016-10-06
Thread moved to the "*Networking & Wireless*" forum, probably a better fit.

---

### Post by jeremy31 on 2016-10-06
We can use the option to see if one antenna works better than the other
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|quality'
```

Then we can try the second antenna option and compare the results from iwlist scan to see if it is better or worse

```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|quality'
```

If ant_sel=1 had better performance use
```
echo "options rtl8723be ant_sel=1" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
```

If ant_sel=2 was better, then 
```
echo "options rtl8723be ant_sel=2" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
```

And you should be set

---

