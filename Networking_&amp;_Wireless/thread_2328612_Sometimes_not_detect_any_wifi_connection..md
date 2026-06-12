---
title: "Sometimes not detect any wifi connection."
date: 2016-06-22
forum: Networking &amp; Wireless
---

### Post by cordourier on 2016-06-22
Hi everywhere, when the computer starts , sometimes not detect any wifi connection.

I have to restart the computer several times to detect WiFi connections.

Could you please help me so that this error does not happen anymore?

some card details:
```

cappy@Dionizo:~$ ifconfig -a
enp5s0    Link encap:Ethernet  HWaddr 00:1e:ec:d0:12:ef  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:15222 (15.2 KB)  TX bytes:15222 (15.2 KB)

wlp4s0    Link encap:Ethernet  HWaddr 00:23:4d:a4:1e:1d  
          inet addr:192.168.15.72  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::e6bc:6a91:8eb1:8453/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2142 (2.1 KB)  TX bytes:15829 (15.8 KB)



04:00.0 Network controller: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
07:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
07:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

root@Dionizo:~# lspci | grep -i ethernet  
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)

root@Dionizo:~# lspci | grep -i network
04:00.0 Network controller: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```



:confused: Thanks for the help :KS

---

