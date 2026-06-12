---
title: "change tcp window size in ubuntu 13.04"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by sunray2 on 2014-03-12
[COLOR=#000000][FONT=Arial]I have 2 ubuntu 13.04 boxes. In between them is a firewall. I did a scp transfer from client to server. After that when I analyze the packets on my firewall using wireshark, I see the window size in the first SYN packet to be 14600. 
If I transfer a very large file, that window size goes all the way to 65535. What I am trying to achieve is to reduce the receive window size to lets say 100 or so to hit the tcp window full condition. What specific tcp parameters I need to change on the ubuntu.[/FONT][/COLOR]
/proc/sys/net/ipv4/tcp_mem:8970 11963   17940
/proc/sys/net/ipv4/tcp_rmem:4096        87380   3092256
/proc/sys/net/ipv4/tcp_wmem:4096        16384   3092256
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

