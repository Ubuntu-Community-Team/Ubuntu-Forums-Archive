---
title: "Run ssh on ports 443 and 80 - need help"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by Nightwalker107 on 2007-07-16
I have a problem, and I'm wonder if someone have a clue.

I'm trying to configure the SSH server (openSSH) of my personal ubuntu computer to listen to port 443 or 80.
When I configure it to "any" other port, like 200, it works fine, but it doesn't works with any of these two ports (443 and 80).

I already tried to open it in iptables:
```
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT
```

With the nMap the port seems be opened:

```
Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-15 00:11 BRT
Interesting ports on XXXXXXXXXXXX.user.veloxzone.com.br (xxx.x.xx.xx):
Not shown: 1696 closed ports
PORT   STATE SERVICE
443/tcp open  http

Nmap finished: 1 IP address (1 host up) scanned in 0.255 seconds
```

When I run the putty from inside my computer(with wine), I can connect with port 443, but when I try from the internet I can't.

The netstats shows this to me:
```
netstat -an --inet
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN
tcp        0      0 192.168.0.3:51034       64.233.179.99:80        ESTABLISHED
tcp        0      0 192.168.0.3:40953       207.46.27.87:1863       ESTABLISHED
tcp        0      0 192.168.0.3:38388       207.46.111.23:1863      ESTABLISHED
tcp        0      0 192.168.0.3:51011       209.85.171.165:80       ESTABLISHED
tcp        0      0 192.168.0.3:42857       64.233.169.99:80        ESTABLISHED
tcp        0      0 192.168.0.3:60971       216.239.51.91:80        ESTABLISHED
udp        0      0 0.0.0.0:32768           0.0.0.0:*
udp        0      0 0.0.0.0:68              0.0.0.0:*
udp        0      0 0.0.0.0:5353            0.0.0.0:*
```

I test the connection to the ports, with one of these port scanners on the net, and when I put port 80, and 443 it couldn't connect. But with port 200 it can.

I already researched on the net, and couldn't find anything to help me. And I need sshd to listen to this ports because only these ports are opened in my college.

Anyone have a clue of where I'm  missing?

Thanks in advance.

---

### Post by kevdog on 2007-07-16
Just wanted to cover the obvious -- you've made the changes in sshd_config and added port lines for port 80 and 443?

---

### Post by Nightwalker107 on 2007-07-16
Hi, yes, I made that change on /etc/ssh/sshd_config file.

Thanks.

---

### Post by kevdog on 2007-07-16
Sorry one more obvious question -- if using a router, you have forwarded ports 80 and 443 to your computer, along with 22?

---

### Post by Nightwalker107 on 2007-07-16
No problem, it is good to cover the obvious... probably the error is obvious and I'm not seeing it.

I'm not using any router, I'm using a moden to connect directly with a DSL connection.

---

### Post by t4thfavor on 2007-07-16
Find out if your running an http server on your pc (already using those ports), and if not then the ISP is probably blocking your the http porty 443, and 80 so you will have to either beg them to stop, or pick a different port.

---

### Post by Nightwalker107 on 2007-07-16
In this case the netstat doesn't had to acuse that this port was occupied?

Anyway, I have almost 90% sure that I'm not running any http server :-k

But now you talk, I'm pretty sure that it is with my ISP.
One time I tried using a router and made a port forwarding from port 443 to port 22, and it didn't work. When I tried with the port forward 200 to 22 it worked. So it is my ISP.

I think I'm a dead end now :(

Anyway, thanks t4thfavor and kevdog to help me to understand the problem. :)

---

