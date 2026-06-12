---
title: "Port is opened and closed at the same time, Mongo server"
date: 2018-01-10
forum: Networking &amp; Wireless
---

### Post by tomwojcik on 2018-01-10
Hi.
I'm moving my Mongo Server from Windows to Ubuntu, but I can't log in via mongo ip:port. I spent over 10 hours debugging this problem but still can't wrap my head around what's wrong.

So I run Mongo on this new Ubuntu. I believe the conf file is ok since it worked fine on Windows. I binded 0.0.0.0.

I flushed iptables and set new rules. Currently ```
iptables -L
``` yields

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             multiport dports domain,http,https,ssh,netbios-ssn,microsoft-ds,netbios-ns,netbios-dgm,27017 ctstate NEW,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             multiport sports domain,http,https,ssh,netbios-ssn,microsoft-ds,netbios-ns,netbios-dgm,27017 ctstate NEW,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  192.168.0.0/24       anywhere            


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             multiport dports domain,http,https,ssh,netbios-ssn,microsoft-ds,netbios-ns,netbios-dgm,27017 ctstate ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             multiport sports domain,http,https,ssh,netbios-ssn,microsoft-ds,netbios-ns,netbios-dgm,27017 ctstate ESTABLISHED
ACCEPT     all  --  anywhere             192.168.0.0/24      
ACCEPT     all  --  192.168.0.0/24       anywhere  

```

I need 27017 to be opened. I've tried multiple approaches with no results, none of the iptables rules work. ```
 nmap -p 27017 -v 192.168.0.175 # Mongo on Ubuntu ip 
``` shows that the port is **closed**, but if I run it locally with ```
 nmap -p 27017 -v 127.0.0.1 
``` it says it's **opened**.

When I nmap Ubuntu-Mongo address I get
```

PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

```
which also surprises me, because I expected more ports to be opened.

At this point security is not my highest concern. I really need to force Ubuntu to allow connection with all computers from the private network. Any tips are highly appreciated.


Additional info:
Client: Ubuntu 16.04, ip: 192.168.0.132
Server: Ubuntu 16.04, ip: 192.168.0.175

mongod.conf contents
```


storage:
  dbPath: /home/username/mongo_data
  directoryPerDB: true
  journal:
    enabled: true


systemLog:
  destination: file
  logAppend: true
  path: /home/username/mongo_logs


net:
  port: 27017
  bindIp: 0.0.0.0


processManagement:
  timeZoneInfo: /usr/share/zoneinfo


security:
  authorization: "enabled"

```

How I've tried to connect:
```
 mongo ip:port 
```
The error I get:
```

MongoDB shell version v3.4.10
connecting to: 192.168.0.175:27017
2018-01-10T11:05:20.897+0100 W NETWORK  [thread1] Failed to connect to 192.168.0.175:27017, in(checking socket for error after poll), reason: Connection refused
2018-01-10T11:05:20.906+0100 E QUERY    [thread1] Error: couldn't connect to server 192.168.0.175:27017, connection attempt failed :
connect@src/mongo/shell/mongo.js:237:13
@(connect):1:6
exception: connect failed

```

I am desperately looking for a solution.

---

### Post by tomwojcik on 2018-01-10
Solved. I had to comment the `bindIp` line from config and add `--bind_ip_all` in terminal when running server.

---

