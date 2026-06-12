---
title: "SCTP RTO calculations in Multihoming"
date: 2015-02-10
forum: Networking &amp; Wireless
---

### Post by bhaktilad on 2015-02-10
[COLOR=#2E3436][FONT=Open Sans]Hi All,[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]Need help in understanding RTO calculations in case of Multi Homing. I am working on one case where RTO timer on primary path are not as expected. [/FONT][/COLOR]
[COLOR=#2E3436][FONT=Open Sans]Expected RTO 0.200 - 0.400 - 0.400 [/FONT][/COLOR]
[COLOR=#2E3436][FONT=Open Sans]Test result RTO 0.200 - 0.280 - 0.400[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]S = Source, PI = Primary IP, SI = Secondary IP[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]Original Packet (S -PI) 23.460597 New Timer 0.2ms started, On laps of this timer first re-transmission on secondary was done. Primary RTO 0.199986[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]First Retransmission (S - SI) 23.660583 New Timer 0.2ms started, On laps of this timer Second retransmission on primary was done. That is after 0.200007 seconds. Thus Secondary RTO 0.200007[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]New Packet (S - PI) 23.740717 New Timer of 400ms started, as new packet on this IP[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]Second Retransmission (S - PI) 23.860590 On laps of Secondary RTO expiry this packet was sent. And no new timer on primary started as already timer is running on this path. [/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]Third Retransmission (S - SI) 24.140604 After 0.399887ms wrth to New packet, another retransmission was done on secondary. But if we compared to above packet its done just after 0.280014ms which means 0.12ms earlier[/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]Forth Retransmission (S - PI) 24.540616 [/FONT][/COLOR]
[COLOR=#2E3436][FONT=Open Sans]Fifth Retransmission (S - SI) 24.940635 [/FONT][/COLOR]
[COLOR=#2E3436][FONT=Open Sans]Sixth Retransmission (S - PI) 25.340654 [/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]The packet arrived at 23.740717 updaetd timer at Primary Transport path. Due to which we can see 4th retransmission done 0.12ms earlier. [/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]As per RFC 4960 - Section 6.3, This behaviour is correct. [/FONT][/COLOR]
[COLOR=#2E3436][FONT=Open Sans]"When an endpoint's peer is multi-homed, the endpoint will calculate a separate RTO for each different destination transport address of its peer endpoint.". [/FONT][/COLOR]
[COLOR=#2E3436][FONT=Open Sans]But in RFC 4960 Section 6.1, this seems to be incorrect, [/FONT][/COLOR]
[COLOR=#2E3436][FONT=Open Sans]"In case of transmission or re-transmission is made to any address, if the T3-rtx timer of that address is not currently running, the sender MUST start that timer. If the timer for that address is already running, the sender MUST restart the timer if the earliest (i.e., lowest TSN) outstanding DATA chunk sent to that address is being retransmitted. Otherwise, the data sender MUST NOT restart the timer". [/FONT][/COLOR]


[COLOR=#2E3436][FONT=Open Sans]Can some one confirm if T3-rtx should be updated if new packet is received on that transport path and re-transmitted packet should follow that timer? [/FONT][/COLOR]

[COLOR=#2E3436][FONT=Open Sans]If the T3-rtx udpates per transport path basis, there wont be any specific pattern of RTO in case of multihoming?[/FONT][/COLOR]


[COLOR=#2E3436][FONT=Open Sans]Regards,[/FONT][/COLOR]
[COLOR=#2E3436][FONT=Open Sans]BL[/FONT][/COLOR]

---

