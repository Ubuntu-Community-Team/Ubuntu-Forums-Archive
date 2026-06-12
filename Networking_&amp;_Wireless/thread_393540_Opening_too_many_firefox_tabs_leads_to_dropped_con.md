---
title: "Opening too many firefox tabs leads to dropped connection"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by Blackie_Chan on 2007-03-25
I have Firefox 2.0.0.3 installed. I connect to my router using a network adapter (D-Link DWL-G122).

Whenever I open more than 10 tabs (each tab loading its contents for a while), my connection drops. 

By saying my connection drops, I mean that the green LED (labelled lnk) on my network turns off, and I'm unable to connect
back onto the computer. 

I've done a number of test, but I have no idea how to fix the problem. My workaround is to restart my computer (every time that I restart the computer I always have a connection). Is there a way to just restart the network part so that I can get a connection again?

Here's what I have from my analysis:

ifconfig rausb0; iwconfig; iwlist (Before Dropped Connection):
```

rausb0    Link encap:Ethernet  HWaddr 00:13:46:6C:97:E7
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe6c:97e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3197777 (3.0 MiB)  TX bytes:266992 (260.7 KiB)

rausb0    RT2500USB WLAN  ESSID:"default"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:0D:88:32:BB:97
          Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-61 dBm  Noise level:-209 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rausb0    Scan completed :
          Cell 01 - Address: 00:0D:88:32:BB:97
                    Mode:Managed
                    ESSID:"default"
                    Encryption key:on
                    Channel:6

```

ifconfig; iwconfig; iwlist (After Dropped Connection):
```

rausb0    Link encap:Ethernet  HWaddr 00:13:46:6C:97:E7
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe6c:97e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9969 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16003485 (15.2 MiB)  TX bytes:1754662 (1.6 MiB)

rausb0    RT2500USB WLAN  ESSID:"default"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-70 dBm  Noise level:-218 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rausb0    No scan results

```

Does anyone know why this is happening? How can I stop it from happenning?

Thanks in advance.

---

### Post by Mr. C. on 2007-03-25
1) Disable IPv6 : [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
2) Update your router's firmware

MrC

---

### Post by Blackie_Chan on 2007-04-01
I found a workaround. I have to physically disconnect the network adapter, then connect it back again. I'll disable ipv6 and hopefully that'll fix my problem.

---

