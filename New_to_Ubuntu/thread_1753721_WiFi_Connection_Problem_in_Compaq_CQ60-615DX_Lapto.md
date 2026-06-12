---
title: "WiFi Connection Problem in Compaq CQ60-615DX Laptop"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by arifinbinmatin on 2011-05-09
Hi,

Recently I have install Kubuntu 11.04 in my Laptop (Compaq CQ60-615DX Notebook) .

I Can manage a Wired Connection But I Can't Get my WiFi Connection.

my ifconfig Response :
```
eth0      Link encap:Ethernet  HWaddr 00:26:2d:be:7b:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:26:2d:be:7b:54  
          inet addr:169.254.7.75  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:42 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24512 (24.5 KB)  TX bytes:24512 (24.5 KB)
``` 

my iwconfig response :
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

Weather i Turn it on or off my WiFi button always remains Red

Looking Forward for possible solutions.

Thanks in Advance 

ARiFiN

---

### Post by Hippytaff on 2011-05-09
Hi and welcome
 
It would also be useful to see the output of lspci or to save time posting results to commands you could run the wireless script by downloading it from the link below, running it and posting the wireless-results.txt

---

