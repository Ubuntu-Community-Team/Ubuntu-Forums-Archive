---
title: "port 22 connection refused"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by localgod11 on 2007-12-21
So i installed openssh-server and rebooted the machine but its still not responding on port22 i keep getting "connection refused" I dont think its the router becasue this in all in my internal network. I have not installed a firewall so I assume I am using the iptables for secuirty (NEWB)

Also when I run  netstat -tulpn i dont see anything on port 22

Also when I run ssh localhost i get connection timed out!

 netstat -tulpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     4525/smbd
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     4865/vino-server
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     4525/smbd
tcp6       0      0 :::8888                 :::*                    LISTEN     5328/sshd
udp        0      0 192.168.2.[COLOR="Red"]X[/COLOR]:137         0.0.0.0:*                          4522/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                          4522/nmbd
udp        0      0 192.168.2.X:138         0.0.0.0:*                          4522/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                          4522/nmbd
udp        0      0 0.0.0.0:177             0.0.0.0:*                          4370/gdm
udp        0      0 0.0.0.0:68              0.0.0.0:*                          4836/dhclient3

---

