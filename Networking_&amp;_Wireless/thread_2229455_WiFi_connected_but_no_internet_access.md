---
title: "WiFi connected but no internet access"
date: 2014-06-13
forum: Networking &amp; Wireless
---

### Post by dmitry22 on 2014-06-13
I am total newbie to linux, so step-by-step instructions with commands and what is expected result would be much appreciated.

WiFi indicates that it is connected, but there is no internet connection. On router it shows that it is connected and provides with IP address: 192.168.1.37, but if I try to ping router from computer or computer from another computer in the net, it says: destination host unreachable.

Tech info:
kernel:
```
uname -a
Linux XXX 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

lspci -nnk:
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Pegatron Device [1b0a:017f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: AzureWave Device [1a3b:1d38]
    Kernel driver in use: rtl8188ee
```

iwconfig:
```
p2p1      no wireless extensions.lo        no wireless extensions.
virbr0    no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:"ZyXEL"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lsmod | grep ^rtl:
```
rtl8188ee              89504  0 
rtlwifi                77765  1 rtl8188ee
```


There are these two threads on the topic:
[http://ubuntuforums.org/showthread.php?t=2192496](http://ubuntuforums.org/showthread.php?t=2192496)
and
[http://ubuntuforums.org/showthread.php?t=2192555&p=12868571#post12868571](http://ubuntuforums.org/showthread.php?t=2192555&p=12868571#post12868571)

but they are concerning another device, and so I don't know how to apply them to my case...

Thanks in advance!

---

### Post by grahammechanical on 2014-06-13
Is the router connected to the Internet Service Provider (ISP)? Linux has done its job when it installs a driver for the network adapter. The ubuntu Network Manager has done its job when it connects the network adapter to the wireless access point/router. But is the router doing its job of connecting to the ISP?

Is there a firewall that is preventing the web browser from going outside of the Local Area Network to the Wide Area Network that is the Internet? And at the same time preventing outside access to the machine.

Regards.

---

### Post by dmitry22 on 2014-06-13
grahammechanical, thank you for the questions,

Router is connected to the ISP, other computers have internet access. So it's not the problem of ISP. As well when i connect this computer through LAN everything works just perfect. It can see other computers and goes online, but when it is connected through wifi, it just gets IP-address from router and nothing else. It can't go to the router's admin page, or even ping router's IP.

It may be so, that there is something in the settings either of router or linux that prevents access. I can only provide example from windows experience: when one connects to the wireless network and selects "public network" option, then computer can't be seen or pinged in that network. May be it's the same here, and I have some firewall in ubuntu, or some wrong settings for wireless conneciton?

---

### Post by dmitry22 on 2014-06-13
One more idea, since LAN interface has IP-address 192.168.1.35 and WiFi 192.168.1.37 could it be so that it is trying to send requests through LAN interface instead of WiFi? Lan is disconnected, but somehow I can still ping 192.168.1.35 from ubuntu. From other computers in the network 192.168.1.35 can't be pinged.

---

### Post by dmitry22 on 2014-06-13
Yep, I blocked LAN interface and everything worked. May be it's not professional at all, but it worked.

Run "ifconfig" to find out interfaces:
```
xxx@yyy:~$ ifconfig
p2p1    Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: XXXX:XXXX:XXXX:XXXX:XXXX/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2511995 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3704518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1241874794 (1.2 GB)  TX bytes:3640666674 (3.6 GB)

```

and then to shut one down:
```
xxx@yyy:~$ sudo ifconfig [*interface]* down
```

---

