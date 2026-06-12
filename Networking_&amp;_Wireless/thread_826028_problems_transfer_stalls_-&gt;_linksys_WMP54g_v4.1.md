---
title: "problems transfer stalls -&gt; linksys WMP54g v4.1  ubuntu 8.04"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by scrape on 2008-06-11
Hello everybody,

I have a linksys WMP54g v4.1 card and ubuntu 8.04 hardy heron installed.  
The first time i ran ubuntu 8.04 my linksys WMP54g v4.1  ran out of the box. I only noticed that my speed was stuck on  1Mb/s. I solved this issue by running ```
sudo iwconfig wlan0 rate 54M 
``` and adding it to ```
/etc/rc.local
```. Now everything runs at 54Mb/s

My problem is the following. Every time I use GFTP or Filezilla to upload files (series) to my modded XBOX the transfers fail almost all the time.
Filezilla states that the reason is due to an Timeout. Gftp states that the transfer/upload stalled. 
 
**What kan de problem be?  How kan i solve this?**

I have the feeling that my wireless connection sometimes temporarily drops. (I am not sure of this).  I did not have this problem prior to installing ubuntu 8.04. I was running ubuntu 7.10 then.  I also didn't change any XBOX settings. I have my network encrypted with WPA personal.


my computer specs:
[LIST]
[*] linksys WMP54g v4.1
[*] IIyama Vision Master Pro 410 Monitor.
[*] ASUS P5B (i965 - S775) motherboard, 
[*] INTEL Core2Duo E6300 (S775 - 1066MHz - 2x1 MB)1,86 CPU ,
[*] PC2-5300 - 1 GB - DDR2 - Kingston ValueRAM CL5.0 RAM, 
[*] Asus EN7600GT/2DHT - 256 MB - PCIe - TV+2xDVI videocard
[*] Samsung 250 GB SP2504C (SATA300 - 8 MB)
[/LIST]

My Network specs:
[LIST]
[*] PC ubuntu 8.04  with linksys WMP54g v4.1 card
[*] WPA personal encrypted
[*] 1 linksys wrt54gl router connected to internet
[*] 1 linksys wrt54gl router installed with (dd-wrt) dat forms a wirelessbridge with the  router connected to internet
[*] XBOX modded plugged into the (dd-wrt) router
[*] NOTE: I have not changed the network config. (only installed ubuntu 8.04) everything was working fine before ubuntu 8.04
[/LIST]

[pc] <--wireless--> [wrt54gl] <--wireless bridge--> [dd-wrt] <-utp-> XBOX

ifconfig output

```
eth0      Link encap:Ethernet  HWaddr 00:18:f3:0a:42:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3898 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:199116 (194.4 KB)  TX bytes:199116 (194.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:70:a5:85:84  
          inet addr:192.168.123.100  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:70ff:fea5:8584/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1444120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2675745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:222057696 (211.7 MB)  TX bytes:3568537060 (3.3 GB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-70-A5-85-84-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

