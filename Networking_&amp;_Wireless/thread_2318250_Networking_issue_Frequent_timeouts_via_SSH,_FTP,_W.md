---
title: "Networking issue? Frequent timeouts via SSH, FTP, Web"
date: 2016-03-24
forum: Networking &amp; Wireless
---

### Post by Sebastian_Becker on 2016-03-24
Hi,

i'm running a Ubuntu 14.04.4 LTS - Server which is located in a data center. I have only remote access to it.

The server is a web server running nginx, php5-fpm and mysql.

Since some time, I have very strange networking issues: 

On - apparently random - clients in my office I get timeouts via SSH, FTP and Web.

SSH-Timeout:
```

$ ssh [sat1nrw.de]("http://sat1nrw.de/") -vv
OpenSSH_6.2p2, OSSLShim 0.9.8r 8 Dec 2011
debug1: Reading configuration data /etc/ssh_config
debug1: /etc/ssh_config line 20: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to [sat1nrw.de]("http://sat1nrw.de/") [46.4.248.26] port 22.
debug1: connect to address 46.4.248.26 port 22: Operation timed out
ssh: connect to host [sat1nrw.de]("http://sat1nrw.de/") port 22: Operation timed out

```

curl Timeout:
```

curl -v [http://www.sat1nrw.de]("http://www.sat1nrw.de/")
* Rebuilt URL to: [http://www.sat1nrw.de/](http://www.sat1nrw.de/)
*   Trying 46.4.248.26...
* connect to 46.4.248.26 port 80 failed: Timed out
* Failed to connect to [www.sat1nrw.de]("http://www.sat1nrw.de/") port 80: Timed out
* Closing connection 0
curl: (7) Failed to connect to [www.sat1nrw.de]("http://www.sat1nrw.de/") port 80: Timed out

```

First strange thing is that PING works:
```

ping [sat1nrw.de]("http://sat1nrw.de/")


Ping wird ausgeführt für [sat1nrw.de]("http://sat1nrw.de/") [46.4.248.26] mit 32 Bytes Daten:
Antwort von 46.4.248.26: Bytes=32 Zeit=12ms TTL=54
Antwort von 46.4.248.26: Bytes=32 Zeit=12ms TTL=54
Antwort von 46.4.248.26: Bytes=32 Zeit=13ms TTL=54
Antwort von 46.4.248.26: Bytes=32 Zeit=12ms TTL=54

```

Second strange thing is, that I can connect on other clients or in certain - apparently random - time windows.

I have no firewall on the server. 
I have confirmed via tcpdump if the server responds to connection attempts.
I have fail2ban installed but I can confirm that the client is not banned.

Thanks, I appreciate any help...

---

