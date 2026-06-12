---
title: "Firestarter: too many blocked connections"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by kitcorey on 2007-10-07
I installed Firestarter when i first installed Ubuntu, and up until recently everything worked fine.  However, recently I have been getting what seems to be far too many blocked connections.  I often recieve more than 30 blocked conenctions per hour, all on the same port: 45173 but from different IP adresses.  I can't seem to find what that port is, or why it would be accesed.  I'm not a firewall expert by any means, and I don't know if this is normal, but certainly does not seem to be.  Should I be worried?

Here is a very short part of a copy of the log:
Time:Oct  7 15:04:56 Direction: Unknown In:eth0 Out: Port:45173 Source:24.22.66.1 Destination:192.168.0.7 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Oct  7 15:04:56 Direction: Unknown In:eth0 Out: Port:45173 Source:89.155.220.244 Destination:192.168.0.7 Length:52 TOS:0x00 Protocol:TCP Service:Unknown
Time:Oct  7 15:05:00 Direction: Unknown In:eth0 Out: Port:45173 Source:71.224.47.54 Destination:192.168.0.7 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Oct  7 15:05:00 Direction: Unknown In:eth0 Out: Port:45173 Source:82.155.172.71 Destination:192.168.0.7 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  7 15:05:01 Direction: Unknown In:eth0 Out: Port:45173 Source:24.28.31.215 Destination:192.168.0.7 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Oct  7 15:05:02 Direction: Unknown In:eth0 Out: Port:45173 Source:24.22.66.1 Destination:192.168.0.7 Length:48 TOS:0x00 Protocol:TCP Service:Unknown

---

