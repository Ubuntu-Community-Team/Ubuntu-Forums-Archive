---
title: "Background Downloads"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Guruprasad on 2010-02-11
Hi

As soon as I start Ubuntu I find using system monitor that some thing is getting downloaded from INTERNET continuously.

Any way to find out which program is downloading stuff?

---

### Post by falconindy on 2010-02-11
You can use `netstat -planut` to find out what has a connection open to the outside world, but you'll need an auxiliary monitor like nethogs to be able to track actual bandwidth usage.

---

### Post by 3rdalbum on 2010-02-11
```
sudo netstat --programs | less
```

Only look under the heading "Active Internet Connections".

Chances are that it's not actually a program hitting the internet - it may be a faulty or weak network driver that keeps trying to renegotiate a connection with your modem or router. If this is the problem, then netstat will not show this connection.

It's probably nothing to worry about too much. It's not like there's any malware that you can get on Linux without running server software.

EDIT: falconindy probably knows more about netstat than me, I had to look it up and work it out just now :-)

---

### Post by Guruprasad on 2010-02-11
netstat -planut gives

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
udp        0      0 0.0.0.0:48730           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               

But still my system monitor shows some receiving data at around 7kbps to 10kbps

---

### Post by Guruprasad on 2010-02-11
sudo netstat --programs | less gives

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path


But still my system monitor shows some receiving data at around 7kbps to 10kbps

---

### Post by mkvnmtr on 2010-02-11
Are you sure it is a download. I found that the browser Chromium it trying to connece to six google servers when I start it. I do not know if they then download because I stopped the connection. There are some apps that will track the address and then you can check who is to find out who you are connectingo to. Also remember that the update manager connects to the repositories daily. I find that it happenes about 10 minutes after I boot on one of my systems.

---

### Post by Guruprasad on 2010-02-11
No Chromium on my system.

Also i disabled the option of connecting to repositories.

---

