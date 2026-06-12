---
title: "Dual NICs and simple routing question"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by peterwilson-69 on 2014-09-24
I need help with a routing issue, please see my simple network diagram. Computer C needs to connect to my internet via computer B, what routing tables do I need on computer B and C?
I don't know how to configure Ubuntu computer C to ping router A. Thank you in advance - I feel like a complete dummy : /

Diagram of my network:
[ATTACH=CONFIG]256667[/ATTACH]

Routing Table of Computer B (Windows 8.1):
```
IPv4 Route Table===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0       10.0.0.138       10.0.0.104     10
         10.0.0.0    255.255.255.0         On-link        10.0.0.104    266
       10.0.0.104  255.255.255.255         On-link        10.0.0.104    266
       10.0.0.255  255.255.255.255         On-link        10.0.0.104    266
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
       172.16.0.0      255.255.0.0         On-link        172.16.0.1    276
       172.16.0.1  255.255.255.255         On-link        172.16.0.1    276
   172.16.255.255  255.255.255.255         On-link        172.16.0.1    276
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link        172.16.0.1    276
        224.0.0.0        240.0.0.0         On-link        10.0.0.104    266
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link        172.16.0.1    276
  255.255.255.255  255.255.255.255         On-link        10.0.0.104    266
```

Routing table of computer C (Ubuntu 12.04):
```
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         172.16.0.1      0.0.0.0         UG    0      0        0 eth0
172.16.0.0      *               255.255.0.0     U     0      0        0 eth0
```

---

### Post by SeijiSensei on 2014-09-24
I believe you need to run [Internet Connection Sharing in Windows]("http://windows.microsoft.com/en-us/windows/set-internet-connection-sharing#1TC=windows-7") to make this happen.

---

### Post by peterwilson-69 on 2014-09-24
Thank you, but that didn't help.

I still can't ping from computer C to router A. I'm not really sure what ICS does (IP Forwarding from 172.16.n.n/16 to 10.0.0.n/24), but it only seemed to change my IP addresses on the 172.16.n.n/16 network and didn't really address the issue (unless I've missed some important concept or failed to explain myself properly - likely). I'll keep trying, thanks.

---

### Post by peterwilson-69 on 2014-09-25
Whoops! my bad - of course your solution worked, you're the expert and I'm the dumb-ass asking questions : )

Nothing worked until I rebooted the Ubuntu computer (weird, cause I did bring the network interface down then up first). Looking at the routing tables, nothing's actually changed. This was a Windows thing that preventing traffic flowing from one nic to the other.

Thanks SeijiSensei : )

---

