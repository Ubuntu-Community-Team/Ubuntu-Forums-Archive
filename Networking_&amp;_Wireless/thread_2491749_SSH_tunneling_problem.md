---
title: "SSH tunneling problem"
date: 2023-10-19
forum: Networking &amp; Wireless
---

### Post by fjk8 on 2023-10-19
Hello,

I have a problem with setup of SSH tunneling, I making tunnel in local machine with:

```
ssh -v -N -R 2222:localhost:22 user@<public ip>
```

tunnel looks proper established:

```
debug1: remote forward success for: listen 2222, connect localhost:22
```

I can connect to tunnel using remote machine with localhost:

```
nc -zv localhost 2222
Connection to localhost (::1) 2222 port [tcp/*] succeeded!
```

but cannot using my public ip:

```
nc -zv <public ip> 2222
nc: connect to <public ip> port 2222 (tcp) failed: Connection refused
```

Ports looks open:

```
netstat -lntu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:2222          0.0.0.0:*               LISTEN
tcp6       0      0 ::1:2222                :::*                    LISTEN
tcp6       0      0 :::80                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 :::21                   :::*                    LISTEN
udp        0      0 127.0.0.53:53           0.0.0.0:*
```

```
lsof -i :2222
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
sshd    4847  fjk    7u  IPv6  53081      0t0  TCP localhost:2222 (LISTEN)
sshd    4847  fjk    9u  IPv4  53082      0t0  TCP localhost:2222 (LISTEN)

```

I'm also set tcpforwarding in /etc/ssh/sshd_config:

```
AllowTcpForwarding yes
```

What I'm doing wrong?
Rehards.

---

### Post by swnjcnewo on 2023-10-19
By default, it will listen on localhost (loopback interface) only. You need to specify the bind_address as 0.0.0.0 in your command:

```
ssh -R 0.0.0.0:2222:localhost:22 TARGET -N
```

[https://serverfault.com/a/861911](https://serverfault.com/a/861911)

---

### Post by fjk8 on 2023-10-23
THANKS! Now it works fine.

---

### Post by fjk8 on 2024-05-08
Is there any way to have real IP's in logs? Now all incoming connections from that tunnel to sshd or Apache are logged as 127.0.0.1 :/
So I cannot use fail2ban for example

---

### Post by TheFu on 2024-05-08
I do port translation on the router, not the VM host.  My VMs have their own LAN IPs.

Also, I use non-standard ports for WAN-side ssh connections. They do get found, but instead of 10,000 attempts/hour, I see just 150 attempts/day.  Fail2ban works.  For example, my logwatch reporting .., from yesterday:
```
Banned services with Fail2Ban:                             Bans:Unbans
    sshd:                                                   [128:85 ]
``` 
And bans for bots scanning my reverse proxy system:

```
 Banned services with Fail2Ban:                              Bans:Unbans
    nginx-botsearch:                                        [  3:3  ]
```

I have different systems for external access for specific reasons.

---

### Post by fjk8 on 2024-06-04
Im use non standard ssh port, but I dont have any router to translate ports, only cable modem with limited options.
Im using ssh tunnel to connect from local machine to remote vps with public ip. Then to make ssh conection from vps to my local one.

---

