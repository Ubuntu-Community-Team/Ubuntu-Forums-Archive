---
title: "IPv6 Stops communication frequently"
date: 2020-04-21
forum: Networking &amp; Wireless
---

### Post by Rajesh_Vaghela on 2020-04-21
Hi All,


I am seeing one issue related to isc-dhcp-server6. It stops communication to UBR10k cmts even though both are on same IPv6 Local network. 

    1. Ubuntu 18.04.4 LTS
    2. Isc-dhcp-server application
    3. IP configuration is give on interfaces with same ethernet has assigned IPv4 and IPv6
    4. CMTS ubr10k has Gigabit ethernet interface has both IP on same interface.
    5. Both systems are communication are connected through Switch on same network.


I tried to look on Networking Module and NetworkManager. I do not see error log. The solution if this issue when I do up down and UP interface through ifconfig eth0 down/Up. It starts working fine.
I am having only IPv communication where IPv5 working fine and never have any issue.

If anybody have any idea, appreciate it. I tried my best and could not find any clue. I do not have any idea where issue is from CMTS or isc-dhcp-server or Network Module. Please let me know

Thanks.

---

