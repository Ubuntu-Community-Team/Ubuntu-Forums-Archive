---
title: "IPtables/Sandvine Question"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by chalewa on 2007-12-19
Ok, I run this script at startup to combat the evilness of sandvine

```
#!/bin/sh
#Replace 6883 with you BT port
BT_PORT=6883

#Flush the filters
iptables -F

#Apply new filters
iptables -A INPUT -i lo -j ACCEPT
#Comcast BitTorrent seeding block workaround
iptables -A INPUT -p tcp --dport $BT_PORT --tcp-flags RST RST -j DROP
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
#BitTorrent
iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport $BT_PORT -j ACCEPT
iptables -A INPUT -m state --state NEW -m udp -p udp --dport $BT_PORT -j ACCEPT
iptables -A INPUT -j REJECT --reject-with icmp-host-prohibited

```

but this then knocks out my samba networking...

anyone know of anything that i could add to the end of this to still alow networking and also have the script still be effective?

thanks

---

