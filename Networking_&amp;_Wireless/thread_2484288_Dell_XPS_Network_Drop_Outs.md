---
title: "Dell XPS Network Drop Outs"
date: 2023-02-22
forum: Networking &amp; Wireless
---

### Post by ghaxby on 2023-02-22
I've been struggling with my network dropping out since getting a Dell XPS last year. I initially thought it was a wifi problem but I've tried with a usb adaptor and I get the same behaviour wired too!

I usually notice in the middle of a slack or teams call, but have noticed when just browsing too. The connection restores it'self after 2-3 minutes.

I have a mix of wired and wireless devices in the house and none of them exhibit the same problem. Infact I usually connect my phone to a teams call at the same time so I stay connected all the time!

I initially followed quite a few posts recommending changing power setting, disabling IPv6, or changing channels, without success.

Any suggestions on how to debug what is going on would be appreciated, as most of the posts with similar behaviours are wifi specific.

syslog errors this morning when the dropout happened look like:

```
Feb 22 09:49:49 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094949.962068:ERROR:stun_port.cc(334)] Port[6574b00:0:1:0:local:Net[enxf8e43b1393eb:192.168.1.x/24:Ethernet:id=1]]: UDP send of 925 bytes to host 52.112.148.x:3480 (52.112.148.x:3480) failed with error 11
Feb 22 09:49:49 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094949.962147:ERROR:stun_port.cc(334)] Port[6574b00:0:1:0:local:Net[enxf8e43b1393eb:192.168.1.x/24:Ethernet:id=1]]: UDP send of 926 bytes to host 52.112.148.x:3480 (52.112.148.x:3480) failed with error 11
Feb 22 09:49:49 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094949.962185:ERROR:stun_port.cc(334)] Port[6574b00:0:1:0:local:Net[enxf8e43b1393eb:192.168.1.x/24:Ethernet:id=1]]: UDP send of 926 bytes to host 52.112.148.x:3480 (52.112.148.x:3480) failed with error 11
Feb 22 09:49:49 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094949.998546:ERROR:stun_port.cc(334)] Port[6574b00:0:1:0:local:Net[enxf8e43b1393eb:192.168.1.x/24:Ethernet:id=1]]: UDP send of 740 bytes to host 52.112.148.x:3480 (52.112.148.x:3480) failed with error 11
Feb 22 09:49:49 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094949.999369:ERROR:stun_port.cc(334)] Port[6574b00:0:1:0:local:Net[enxf8e43b1393eb:192.168.1.x/24:Ethernet:id=1]]: UDP send of 641 bytes to host 52.112.148.x:3480 (52.112.148.x:3480) failed with error 11
Feb 22 09:49:49 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094949.999496:ERROR:stun_port.cc(334)] Port[6574b00:0:1:0:local:Net[enxf8e43b1393eb:192.168.1.x/24:Ethernet:id=1]]: UDP send of 641 bytes to host 52.112.148.x:3480 (52.112.148.x:3480) failed with error 11
Feb 22 09:49:49 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094949.999600:ERROR:stun_port.cc(334)] Port[6574b00:0:1:0:local:Net[enxf8e43b1393eb:192.168.1.x/24:Ethernet:id=1]]: UDP send of 52 bytes to host 52.112.148.x:3480 (52.112.148.x:3480) failed with error 11
Feb 22 09:49:50 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094950.030147:ERROR:stun_port.cc(334)] Port[6574b00:0:1:0:local:Net[enxf8e43b1393eb:192.168.1.x/24:Ethernet:id=1]]: UDP send of 1134 bytes to host 52.112.148.x:3480 (52.112.148.x:3480) failed with error 11
Feb 22 09:49:51 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094951.307777:ERROR:connection.cc(726)] Conn[fc88c00:0:Net[enxf8e43b1393eb:192.168.1.x/24:Ethernet:id=1]:i8GlVXdc:1:0:stun:udp:81.132.76.x:44355->SLaNrqjV:1:54001663:relay:udp:52.112.148.x:3480|CRWI|S|0|0|231935379886587391|36]: Failed to send STUN BINDING response, to=52.112.148.x:3480, err=-1, id=2beae40374e5b493fce04c74
Feb 22 09:49:54 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094954.176690:ERROR:stun_port.cc(632)] UDP send of 20 bytes to host euaz.relay.teams.microsoft.com:3478 (52.114.227.x:3478) failed with error 11: [0x0000000b] Resource temporarily unavailable
Feb 22 09:49:54 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094954.688689:ERROR:stun_port.cc(632)] UDP send of 20 bytes to host euaz.relay.teams.microsoft.com:3478 (52.114.227.x:3478) failed with error 11: [0x0000000b] Resource temporarily unavailable
Feb 22 09:49:55 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094955.668591:ERROR:connection.cc(726)] Conn[fc88c00:0:Net[enxf8e43b1393eb:192.168.1.x/24:Ethernet:id=1]:i8GlVXdc:1:0:stun:udp:81.132.76.x:44355->SLaNrqjV:1:54001663:relay:udp:52.112.148.x:3480|CRwI|S|0|0|231935379886587391|36]: Failed to send STUN BINDING response, to=52.112.148.x:3480, err=-1, id=175af7a110af7eb5151b0cdc
Feb 22 09:49:55 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094955.704676:ERROR:stun_port.cc(632)] UDP send of 20 bytes to host euaz.relay.teams.microsoft.com:3478 (52.114.227.x:3478) failed with error 11: [0x0000000b] Resource temporarily unavailable
Feb 22 09:49:57 GrahamsXPS msedge-cifhbcnohmdccbgoicgdjpfamggdegmo-Default.desktop[12385]: [40714:32:0222/094957.720672:ERROR:stun_port.cc(632)] UDP send of 20 bytes to host euaz.relay.teams.microsoft.com:3478 (52.114.227.x:3478) failed with error 11: [0x0000000b] Resource temporarily unavailable

```

---

### Post by TheFu on 2023-02-22
Are you using a VPN?

---

### Post by ghaxby on 2023-02-23
No

---

### Post by TheFu on 2023-02-23
I put the error into google and got lots of results for this error. One is:
[https://support.microsoft.com/en-us/office/my-teams-calls-keep-dropping-85d32f67-3310-46b4-aed3-b7310cccc7c9](https://support.microsoft.com/en-us/office/my-teams-calls-keep-dropping-85d32f67-3310-46b4-aed3-b7310cccc7c9)

When the connection drops, test all other connections to see where the break is happening.  
[LIST]
[*]Can you ping your router?
[*]Can you ping other devices on your LAN?
[*]Can you ping google.com?
[*]Can you ping 8.8.8.8?
[*]Can you visit other websites?
[*]Can you visit other MSFT websites?
[*]Keep track of what works and what doesn't.
[/LIST]


Basic network troubleshooting.

---

### Post by ghaxby on 2023-02-23
[COLOR=#000000]I've been googling for months!
[/COLOR]

[LIST]
[*]Can you ping your router? NO
[*]Can you ping other devices on your LAN? NO
[*]Can you ping google.com? NO
[*]Can you ping 8.8.8.8? NO
[*]Can you visit other websites? NO
[*]Can you visit other MSFT websites? NO
[*]Keep track of what works and what doesn't. When it fails I can't ping anything other than localhost, no obvious syslog errors, it's all network interfaces.

This isn't a problem with teams, as I said it happens with other apps like slack, or just browsers like chrome, and any commands.

If you can can google multiple network interfaces failing at the same time and share any steps to diagnose that would really help.

Thanks
[/LIST]

---

### Post by TheFu on 2023-02-23
Well, then I'd move to hardware incompatibilities, drivers, settings, and physical connections.

Simplify and test.  Repeat.
Start with the basics.  Use static IPs, not DHCP.
Only use wired ethernet, not wifi.
Check all your network settings, drivers, cables, switch ports. Don't use any power saving or sleep or WoL modes. If you are using DHCP, what is the lease period? Do the renewals align with lost connections?
If you post the exact drivers and hardware used, someone might recognize known issues.

OT:
My LUG use to meet at a restaurant that had a netgear wifi router.  We'd all be disconnected separately all the time - like 3x over a 2 hour meeting.  I convinced the owner to allow us to replace the wifi with better quality hardware and that fixed the issue.  Because 10 people were having issues, we knew it wasn't with all our Linux setups, but with something in the netgear settings.  I suppose we could have fought to solve it in those settings, but at the time, getting a new AP from a reputable, small business wifi vendor was only $50. We all chipped in $5/ea. The business had better wifi for 20+ connections too, which most home routers just aren't able to handle.  Fortunately, we had no issue with the wired connections ... since we weren't using any. Those worked fine.

I don't use teams, slack nor chrome, not that it should matter, but sometimes programs think they are "standards" and ignore other standards wrongly.

---

