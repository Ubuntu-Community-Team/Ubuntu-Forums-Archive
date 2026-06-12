---
title: "Network Monitoring program"
date: 2016-07-25
forum: Networking &amp; Wireless
---

### Post by secoonder on 2016-07-25
&#304; am using iptables+ squid proxy server in my firewall. i can see 80. port trafic in squid logs.
But i can not other ports.
i think wireshark is not useful program.
**i want to see package size,source ip+destination ip +source port +dest port etc...**
i think top,htop,tcpdump is very single program
Which program is best useful?

---

### Post by The Cog on 2016-07-25
Which is most useful depends on what you are trying to do. top and htop don't show packets at all. They show processes.
If you want to see packet sizes, IP addresses and ports, tcpdump is good. You might also like iftop or ntop.
Why do you want to see this information? Problem debugging, throughput monitoring?

Wireshark is incredibly useful if you want to know more than just IP addresses and port numbers.

---

