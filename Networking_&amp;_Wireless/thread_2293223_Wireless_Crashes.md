---
title: "Wireless Crashes"
date: 2015-09-03
forum: Networking &amp; Wireless
---

### Post by krisskobi on 2015-09-03
Hi all :)

I was wondering if you could help me please: my wireless crashes randomly, I've tried different wireless networks. Sometimes forgetting network and rest helps, sometimes not. Sometimes I just press connect again and it connects, sometimes I spend a long time before I can get it back to work. As you can imagine it can be rather frustrating when I need to access information from Internet urgently before exiting house.

I have MSI MS-16GD laptop.

I'd very much appreciate your help.

These are results from:
[B]
uname -r[/B]

3.16.0-46-generic
[B]
lspci -nn | grep -e 0200 -e 0280[/B]

04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]

**ifconfig**

eth0      Link encap:Ethernet  HWaddr 44:8a:5b:44:02:a8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:117091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117091 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:122419526 (122.4 MB)  TX bytes:122419526 (122.4 MB)

wlan0     Link encap:Ethernet  HWaddr 54:27:1e:67:4c:c7  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5627:1eff:fe67:4cc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:196637 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:257720283 (257.7 MB)  TX bytes:17401300 (17.4 MB)


Kind regards,

Chris

---

