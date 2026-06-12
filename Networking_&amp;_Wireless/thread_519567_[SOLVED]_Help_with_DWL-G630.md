---
title: "[SOLVED] Help with DWL-G630"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by dpw700 on 2007-08-07
I've just installed 7.04 out of the box.
Got a DLINK DWL-G630

lspci -v shows:

03:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc D-Link AirPlus G DWL-G630 Wireless Cardbus Adapter(rev.D)
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at d4000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2


The network settings gui shows the card, and appears to be connected (tho I'm not sure how you tell this).

ifconfig:

ath0      Link encap:Ethernet  HWaddr 00:11:95:92:92:12  
          inet6 addr: fe80::211:95ff:fe92:9212/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:11:95:92:92:12  
          inet addr:169.254.5.148  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


iwconfig showed:

ath0      IEEE 802.11g  ESSID:"DPWRTR"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/94  Signal level=-56 dBm  Noise level=-96 dBm
          Rx invalid nwid:116481  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist ath0 scan:
ath0      Scan completed :
          Cell 01 - Address: 00:0F:3D:A7:B6:30
                    ESSID:"DPWRTR"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/94  Signal level=-59 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:0F:3D:A7:B6:30
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/94  Signal level=-58 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100


If I pull out the wire and/or stop the wired connection I can't see anything, eg

When I ping the router
 ping 10.1.1.1
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data.
From 169.254.5.148 icmp_seq=1 Destination Host Unreachable

I'm lost, what's happening?

- why is there 2 cells showing my router mac address?
- what is ath0:avah, the thing at the end of 169.254.5.148?

Some updates:

I changed the wireless connection so that the 'roaming' was enabled. When I deactivated the wire connection and activated the wireless conn to my router the signal strengh bars appeared. But the dhclient still can't get an address.

Help!!

By the way how do I get these silly smiley's out of the message?

Thanks,

Darren

---

