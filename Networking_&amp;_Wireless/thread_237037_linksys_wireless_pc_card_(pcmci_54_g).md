---
title: "linksys wireless pc card (pcmci 54 g)"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by hypnus on 2006-08-15
I am having rather strange results with this card, and I am already looking for a few days for a solution.  I blacklisted bcm45xx to DISABLE native ubuntu support, used ndiswrapper, (it says installed and hardware present) using WIFI radar (wireless network tool gives ALL networks in my neighbourhoud, detects my network)

BUT

When trying to connect my router LOG Sees this laptop, WIFI RADER SAYS connected as my router confirms, but NO IP IS GIVEN AND WHEN I GIVE ONE MANUA L THERE IS NO WORKING CONNECTIONS

The access point not associated is is normal, because i am working now using regular cable and had to disable wirless to type this message.

ANYONE ANY IDEA TRIED ALREADY DHCLIENT WLAN1 !!! TIMES OUT!! Seems that dhcp is not working ...

Getting desperate, seeing networks wich it connects without having really a working connection.. PING results are no good..

Some command line results:

iwconfig:

wlan1     IEEE 802.11g  ESSID:off/any  Nickname:"JVDB"
          Mode:Auto  Frequency:2.452 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:16 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
ifconfig:

wlan1     Link encap:Ethernet  HWaddr 00:0F:66:CF:69:8E
          inet6 addr: fe80::20f:66ff:fecf:698e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:135702 (132.5 KiB)
          Interrupt:11 Memory:c2000000-c2002000

ndiswrapper -l

Installed ndis drivers:
bcmwl5          driver present, hardware present

---

