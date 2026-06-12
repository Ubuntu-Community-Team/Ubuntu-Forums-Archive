---
title: "HOWTO: make conky display ppp0 connection info only if connected"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by bimmerd00d on 2007-06-02
Just add thisto your .conkyrc where you want it displayed and there you have it, a wealth of connection info including IP address, current transfer speeds, and a graph.  Change "Cingular GPRS" to whatever you want for a title.

```
${if_running pppd}
${color #ffcb48}Cingular GPRS$color ${color #ffcb48}${stippled_hr}$color
 ${color #98c2c7}WAN IP (${addr ppp0})$color
 download ${color green}${downspeed ppp0}kb/s$color $alignr upload ${color red}${upspeed ppp0}kb/s
${color #c2c798}${downspeedgraph ppp0 25,140 1d761b 5faa00}$alignr${upspeedgraph ppp0 25,140 761d1b ca7f1a}$color $endif
```

---

