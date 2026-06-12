---
title: "Firestarter block connectiongs that shouldent even be there"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by SpinningAround on 2007-10-30
I have a router with a firewall that have port A port forwarded, there is no other computers running on the local network. The things is that firestarter show blocks for port B so where do that connection come from?

I have checked the connections and they are both external and not from anything within the local network.

---

### Post by shane2peru on 2007-10-30
I keep getting hit from outside as well here is my event log:
```

Time:Oct 30 14:16:47 Direction: Unknown In:eth0 Out: Port:32895 Source:200.48.225.133 Destination:192.168.78.170 Length:159 TOS:0x00 Protocol:UDP Service:Sun-RPC portmap
Time:Oct 30 14:23:40 Direction: Unknown In:eth0 Out: Port:32946 Source:200.48.225.133 Destination:192.168.78.170 Length:128 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct 30 14:43:58 Direction: Unknown In:eth0 Out: Port:32988 Source:200.48.225.133 Destination:192.168.78.170 Length:128 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct 30 14:55:08 Direction: Unknown In:eth0 Out: Port:33056 Source:200.48.225.133 Destination:192.168.78.170 Length:122 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct 30 14:55:20 Direction: Unknown In:eth0 Out: Port:33054 Source:200.48.225.133 Destination:192.168.78.170 Length:67 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct 30 16:14:21 Direction: Unknown In:eth0 Out: Port:33137 Source:jungle.metalab.unc.edu Destination:192.168.78.170 Length:1482 TOS:0x00 Protocol:TCP Service:Unknown
Time:Oct 30 16:19:20 Direction: Unknown In:eth0 Out: Port:33140 Source:200.48.225.133 Destination:192.168.78.170 Length:158 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct 30 16:25:22 Direction: Unknown In:eth0 Out: Port:49228 Source:152.46.7.109 Destination:192.168.78.170 Length:1482 TOS:0x00 Protocol:TCP Service:Unknown
Time:Oct 30 16:27:12 Direction: Unknown In:eth0 Out: Port:33147 Source:200.48.225.133 Destination:192.168.78.170 Length:132 TOS:0x00 Protocol:UDP Service:Unknown

```
You will notice they are by the same people over and over again, trying other ports.  Also I ran this check:  
[http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2)

And it tells me my port 23 is open - telnet.  How can I close that?  I tried closing it via the router, but apparently that didn't do it.

Shane

---

