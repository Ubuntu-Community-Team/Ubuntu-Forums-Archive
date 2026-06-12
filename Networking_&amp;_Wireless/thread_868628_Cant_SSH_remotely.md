---
title: "Cant SSH remotely"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by kambodianboi on 2008-07-24
Hey guys,

I setted up my linux PC for my gaming server. I installed SRCDS, and SSH successfully. SRCDS had an issue with being visible to the internet, which was fixed with SRCDS parameter +ip <eth0 IP>. But I think my SSH server is having the same issue.

I can access SSH locally, and on the same network (ie. 192.168.1.150 being the linux PC). But when I enter my external IP (ie. 71.125.145.2) to access linux PC, it shows connection refused. I have my router port forwarded (port 22) to the linux PC. But still no luck.

I checked netstat and it shows

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address
State       PID/Program name
tcp        0      0 192.168.1.150:27015     0.0.0.0:*
LISTEN      12602/srcds_i686
tcp        0      0 127.0.0.1:3306          0.0.0.0:*
LISTEN      5942/mysqld
tcp        0      0 0.0.0.0:80              0.0.0.0:*
LISTEN      6443/apache2
tcp        0      0 0.0.0.0:21              0.0.0.0:*
LISTEN      6362/proftpd: (acce
tcp        0      0 0.0.0.0:22              0.0.0.0:*
LISTEN      12261/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*
LISTEN      6042/cupsd
tcp        0      1 192.168.1.150:55565     68.142.88.34:27038
SYN_SENT    12602/srcds_i686

SRCDS shows that its listening to 192.168.1.150 (eth0), but SSH shows its listening to all network device (I assume)

And its not just SSH, also Apache, ProFTP have the same issue... Can be access on the network, but not externally. All ports on the router have been forwarded.

Any help would be much appreciated!

---

### Post by superprash2003 on 2008-07-24
do you have firestarter or anything similar running?

---

### Post by kambodianboi on 2008-07-24
I do, but it does not see any inbound connection for SSH or Apache. Only if I connect locally. Even if its Disable, still no luck.

---

