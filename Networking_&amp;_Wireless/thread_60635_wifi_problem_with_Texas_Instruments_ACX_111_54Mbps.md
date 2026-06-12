---
title: "wifi problem with Texas Instruments ACX 111 54Mbps Wireless Interface"
date: 2005-08-28
forum: Networking &amp; Wireless
---

### Post by suoko on 2005-08-28
hi,

I have a packard bell easy note b3510 and i can't connect with the integrated wifi card.
this is the lspci output,
0000:00:0a.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
while windows hardware admin says it's a TNET1130.

the gnome network tool shows the wifi card and also try to scan networks but unfortunately it doesn't find any although I'm sure there's one (windows can connect to it)
the connection is without any encryptions.

**iwconfig output:**

lo        no wireless extensions.

wlan0     IEEE 802.11g/b+  ESSID:"G604T_wireless"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


**ifconfig output :**
eth0      Link encap:Ethernet  HWaddr 00:40:D0:74:37:19
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe74:3719/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:231674840 (220.9 MiB)  TX bytes:11073895 (10.5 MiB)
          Interrupt:23 Base address:0xe200

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:300060 (293.0 KiB)  TX bytes:300060 (293.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          inet6 addr: ::192.168.1.3/96 Scope:Compat
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:74 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:60:B3:D2:18:E6
          inet6 addr: fe80::260:b3ff:fed2:18e6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18



How can I know the driver which ubuntu is using is fine?

---

### Post by suoko on 2005-08-31
[QUOTE=suoko]hi,

I have a packard bell easy note b3510 and i can't connect with the integrated wifi card.
this is the lspci output,
0000:00:0a.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
while windows hardware admin says it's a TNET1130.

the gnome network tool shows the wifi card and also try to scan networks but unfortunately it doesn't find any although I'm sure there's one (windows can connect to it)
the connection is without any encryptions.

**iwconfig output:**

lo        no wireless extensions.

wlan0     IEEE 802.11g/b+  ESSID:"G604T_wireless"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


**ifconfig output :**
eth0      Link encap:Ethernet  HWaddr 00:40:D0:74:37:19
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe74:3719/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:231674840 (220.9 MiB)  TX bytes:11073895 (10.5 MiB)
          Interrupt:23 Base address:0xe200

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:300060 (293.0 KiB)  TX bytes:300060 (293.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          inet6 addr: ::192.168.1.3/96 Scope:Compat
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:74 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:60:B3:D2:18:E6
          inet6 addr: fe80::260:b3ff:fed2:18e6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18



How can I know the driver which ubuntu is using is fine?[/QUOTE]
 I found out the card is a mini pci XG650. I tried all possibile drivers provided by linuxant for all variants of texas instruments chipset both with linuxant and ndiswrapper with no success. I also tried the working drivers located in my windows drivers directory again with no success. What can I do???

---

### Post by mattisf on 2006-01-02
I got a Zyxel card that's based on the same chipset. I had to unload the acx_pci module before I could make the ndiswrapper work. It seems the acx_pci module is really buggy... :-/ 

So:

sudo modprobe -r acx_pci
sudo ndiswrapper -i [your windows driver here]

Maybe you tried this already. Just in case you didn't... :-)

Cheers,

Mattis

---

