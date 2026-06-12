---
title: "Another ipw2200 victim on Edgy"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by MaraMax on 2006-11-18
I installed a fresh Edgy on my laptop a week ago.
It's a centrino so it uses the famous Intel Corporation PRO/Wireless 2200BG Network Connection and it don't connect anymore.

I tried the 2.6.18.2 kernel and also I installed ieee80211-1.2.15, ipw2200-1.2.0 and ipw2200-fw-3.0 from ipw2200.sourceforge.

Here are my details:

```

lsmod|grep ieee
ieee80211              50284  1 ipw2200
ieee80211_crypt         6528  1 ieee80211
ieee1394              302648  2 sbp2,ohci1394
```

```

dmesg|grep ipw
[   19.692000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0
[   19.692000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.692000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   20.560000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a 
```

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"galaxy"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:04:ED:23:CD:7F
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-33 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

```

iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:04:ED:23:CD:7F
                    ESSID:"galaxy"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 54 Mb/s
                    Quality=87/100  Signal level=-42 dBm
                    Extra: Last beacon: 4304ms ago

```

```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:02:95:CE
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe02:95ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5681 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4749281 (4.5 MiB)  TX bytes:695759 (679.4 KiB)
          Interrupt:5 Base address:0xcc00

eth1      Link encap:Ethernet  HWaddr 00:12:F0:65:9F:40
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.255
          inet6 addr: fe80::212:f0ff:fe65:9f40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1356 (1.3 KiB)  TX bytes:432 (432.0 b)
          Interrupt:5 Base address:0x2000 Memory:fe8fe000-fe8fefff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1624 (1.5 KiB)  TX bytes:1624 (1.5 KiB)
```

```

lspci|grep Net
01:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
```

When i try to ping my router 
```
ping 192.168.1.254
connect: Network is unreachable
```
That's all.
On Dapper it works good.

---

### Post by n3Cre0 on 2006-11-18
Sorry if I was giving you false hope by posting but I just wanted to ask a question.

I also got the ipw2200B/G Pro (and Edgy) but here is everything fine. Is it a hardware error? Or will I get the same within X days?
Did it ever work?

---

### Post by MaraMax on 2006-11-19
What can I say...I don't know.
However imo this is not a hardware error.
My Edgy has worked for few days than I had some problems with kopete and so on...

---

