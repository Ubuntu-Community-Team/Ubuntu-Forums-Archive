---
title: "Firestarter Problems"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by Jawshie on 2008-09-22
When I have Firestarter enabled, I am unable to use local network host names to connect to other machines and I am unable to browse the network. I can still use IP addresses to connect but this is not very convenient. When it is off, everything works fine. What can I do to allow Firestarter to be enabled and still have this capability?

---

### Post by Kylibar on 2008-11-21
i had sugery this afternoon on 1 hand, so please 4give 4 typos n stuff

i know nothing of firestarter (its an iptables front end right?)

i use shorewall but i might b able to help. you have to enable SMB sharing on the interface routes u want sharing enabled on. it sounds like firestarter is "rejecting" the "rule or policy" of SMB sharing. u need to enable ports;

[HTML]
(windows file sharing)
tcp 139
tcp 445
udp 137
udp 138

i forgot what the smb ports arw for linux
[/HTML]

anyway, u need to enable the sharing ports on your linux box. sorry i cant walk u thru it, i know nothing of firestarter. hope i helped

---

