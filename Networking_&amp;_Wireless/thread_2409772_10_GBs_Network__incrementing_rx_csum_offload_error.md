---
title: "10 GBs Network | incrementing rx_csum_offload_errors via ethtool"
date: 2019-01-06
forum: Networking &amp; Wireless
---

### Post by madhavramdin on 2019-01-06
**I have just changed to a 10GB switch in my LAN - all our servers are now communicating well (at first glance):**

:~$ ethtool ens4
Settings for ens4:
	Supported ports: [ TP ]
	Supported link modes:   1000baseT/Full 
	                        10000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  100baseT/Full 
	                        1000baseT/Full 
	                        10000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 10000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: external
	Auto-negotiation: on
	MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: yes


**Moreover, doing an iperf test to any internal server does show this:**

[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  10.9 GBytes  9.32 Gbits/sec



Upon deeper inspection, I can see that errors on the NICs are incrementing


~$ ethtool -S ens4 | grep error
     rx_errors: 0
     tx_errors: 0
     rx_over_errors: 0
     rx_crc_errors: 0
     rx_frame_errors: 0
     rx_fifo_errors: 0
     rx_missed_errors: 0
     tx_aborted_errors: 0
     tx_carrier_errors: 0
     tx_fifo_errors: 0
     tx_heartbeat_errors: 0
     rx_long_length_errors: 0
     rx_short_length_errors: 0
[B]     rx_csum_offload_errors: 2352



[/B]At first, I thought it was an issue with the ring settings, go I pushed it to the max:


~$ ethtool -g ens4
Ring parameters for ens4:
Pre-set maximums:
RX:       4096
RX Mini:  0
RX Jumbo: 0
TX:       4096
Current hardware settings:
RX:       4096
RX Mini:  0
RX Jumbo: 0
TX:       4096




I am now stuck -- after doing some research, I understand that enabling flow control and jumbo packets can help in these cases.
As this is a production environment, I would like your advice on this issue.

---

