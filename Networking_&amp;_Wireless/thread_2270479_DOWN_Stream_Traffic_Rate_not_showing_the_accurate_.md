---
title: "DOWN Stream Traffic Rate not showing the accurate value by using VNSTAT tool"
date: 2015-03-23
forum: Networking &amp; Wireless
---

### Post by PavanKolli on 2015-03-23
Hi

We integrated **Vnstat** open source tool to calculate the US&DS Speed test data rates for the WAN ports in our product.

But This tool returns,
DownStream Throughput data with 10%-8% tolerance.
UownStream Throughput data is accurate of the input data rate.

I am using spirent test center to pump traffic for both UP Stream and Down Stream.

No packet loss occure, in STC I am getting the correct rate of traffic in both sides.

Only in the VNSTAT tool giving some deviation traffic rate in the down stream side.
[TABLE="class: grid, width: 500"]
[TR]
[TD][/TD]
[TD]In STC[/TD]
[TD]In WEB[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE="width: 260"]
[TR="class: grid"]
[TD]          TX[/TD]
[TD]     RX[/TD]
[/TR]
[TR="class: grid"]
[TD]8.6 MbPS[/TD]
[TD]8.6 Mbps[/TD]
[/TR]
[TR="class: grid"]
[TD]8.6 Mbps[/TD]
[TD]8.3 Mbps[/TD]
[/TR]
[/TABLE]
[/TD]
[TD]Throughput Values[/TD]
[/TR]
[TR]
[TD]UP Stream[/TD]
[TD]US Throughput  8.4 Mbps[/TD]
[/TR]
[TR]
[TD]Down Stream[/TD]
[TD]DS Throughput  7.3 Mbps[/TD]
[/TR]
[/TABLE]



But some tolerance observed in the for the Downstream side RX Bytes in terms of bits/second.


**_VNSTAT Dump:_**

AONT3@:/ # vnstat -i pon_60_0_1 -tr 10
168648 packets sampled in 10 seconds
Traffic average for pon_60_0_1

rx 7.25 Mbit/s 8432 packets/s
tx 8.70 Mbit/s 8432 packets/s

if you see the above dump, Tx & Rx both have same number of packets/second and it have different data rates.

Can any one help me to find the issue.
 
Thanks & Regards
Pavan Kumar Kolli
office: +91 44 3312 8141 (Ext:8141)
Personal: +91 9952 083086

---

