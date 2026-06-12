---
title: "Need better control over programs using network devices."
date: 2022-09-28
forum: Networking &amp; Wireless
---

### Post by samuli-latvala on 2022-09-28
I am sorry if topic is already covered. Don't really know anymore what to search after 2 sleepless nights over the topic (just now figured out what is wrong). 

I have private server and some programs (game servers) that should listen specific device for incoming traffic. Poth programs are launch during the boot and one or both work 10% of the time and here is the obvious reason: 

```
@node2:~/scripts$ sudo netstat -peanutActive Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode      PID/                                                                                                                                   Program name
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      102        26668      654/                                                                                                                                   systemd-resolve
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      0          26933      735/                                                                                                                                   sshd: /usr/sbin
tcp        0      0 192.168.0.7:46257       155.133.230.50:27021    ESTABLISHED 1001       34935      1665                                                                                                                                   /./ProjectZombo
tcp        0      0 192.168.0.7:51807       155.133.230.34:27032    ESTABLISHED 1001       32064      1594                                                                                                                                   /./valheim_serv
tcp        0      0 192.168.0.6:22          192.168.0.11:51549      ESTABLISHED 0          26960      802/                                                                                                                                   sshd: samsunix
tcp6       0      0 :::27015                :::*                    LISTEN      1001       32125      1665                                                                                                                                   /./ProjectZombo
tcp6       0      0 :::22                   :::*                    LISTEN      0          26935      735/                                                                                                                                   sshd: /usr/sbin
udp        0      0 0.0.0.0:16261           0.0.0.0:*                           1001       32119      1665                                                                                                                                   /./ProjectZombo
udp        0      0 127.0.0.53:53           0.0.0.0:*                           102        26667      654/                                                                                                                                   systemd-resolve
udp        0      0 192.168.0.6:68          0.0.0.0:*                           101        26344      652/                                                                                                                                   systemd-network
udp        0      0 192.168.0.7:68          0.0.0.0:*                           101        26338      652/                                                                                                                                   systemd-network
udp        0      0 0.0.0.0:2458            0.0.0.0:*                           1001       34888      1594                                                                                                                                   /./valheim_serv
udp6       0      0 :::2457                 :::*                                1001       34899      1594                                                                                                                                   /./valheim_serv
```

How can I better manage which device program should listen when there is no obvious settings on program itself? All help appreciated.

---

