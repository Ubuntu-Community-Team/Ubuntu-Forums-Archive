---
title: "tcpdump"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by jnorthr on 2007-11-02
You may or may not remember there is a command we can use to discover the flow of TCP/IP messages across our wireless networks and that command is [COLOR="DarkOrchid"]tcpdump[/COLOR]. If you have what you feel is a working-ish connection, then from a terminal command line for example, try:

**sudo tcpdump -i wlan0**

replacing wlan0 with your interface name. An audit trail will result  from all the messages flowing across the wlan0 interface. Then if you really need to dig into the nitty-gritty, look at [http://www.eventhelix.com/RealtimeMantra/Networking/](http://www.eventhelix.com/RealtimeMantra/Networking/)

Two points to note:
1) this process only monitors but does not change any packets or data
2) some interfaces cards may not support promiscuous modes to 'look' for all possible nodes - that means it cannot be used to send/receive packets while at the same time trying to monitor for them. For that purpose, you need a third system to just listen in on the network using [COLOR="DarkOrchid"]tcpdump[/COLOR]

---

