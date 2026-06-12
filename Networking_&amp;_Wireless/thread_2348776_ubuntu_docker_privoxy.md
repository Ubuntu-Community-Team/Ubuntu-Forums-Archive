---
title: "ubuntu docker privoxy"
date: 2017-01-07
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2017-01-07
installed apt-get install docker.io

sudo docker pull ubuntu

sudo docker run -it --name privoxy0 ubuntu /bin/bash

inside docker
root@ac68f405042d:# apt-get update; apt-get install aptitude wget nano axel iptables privoxy less
used [https://help.ubuntu.com/community/DansGuardian](https://help.ubuntu.com/community/DansGuardian) to configure privoxy using port 8118
listen-address 127.0.0.1:8118
root@ac68f405042d:# service privoxy start
root@ac68f405042d:# exit 

sudo docker commit privoxy0 local:privoxy1

when I set the browser for 127.0.0.1 port 8118 it dose not work so what I'm I doing wrong?

---

### Post by lance bermudez on 2017-01-08
sudo docker run -it -p 8118:8118 --name privoxy0 local:privoxy010717 /bin/bash
inside docker container
```

root@801a3f014117:/# service privoxy status
 * privoxy is not running
root@801a3f014117:/# service privoxy start 
 * Starting filtering proxy server privoxy                                                                                   [ OK ] 
root@801a3f014117:/# ifconfig
eth0      Link encap:Ethernet  HWaddr 02:42:ac:11:00:02  
          inet addr:172.17.0.2  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::42:acff:fe11:2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:187676 (187.6 KB)  TX bytes:9308 (9.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

How do I get the proxy port to work? I have my browser set for 127.0.0.1:8118 and it dose not work.

---

### Post by lance bermudez on 2017-01-18
Firewalld is the problem I think dose any one know of a fix?
```

&#9679; firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/lib/systemd/system/firewalld.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2017-01-18 12:39:50 MST; 1h 47min ago
 Main PID: 1304 (firewalld)
    Tasks: 2
   Memory: 3.5M
      CPU: 2.930s
   CGroup: /system.slice/firewalld.service
           &#9492;&#9472;1304 /usr/bin/python3 -Es /usr/sbin/firewalld --nofork --nopid

Jan 18 12:40:09 Tardis /firewalld[1304]: ERROR: COMMAND_FAILED: '/sbin/iptables -w2 -t nat -C OUTPUT -m addrtype --dst-type LOCAL -j DOCKER ! --dst 127.0.0.0/8' failed: iptables: No chain/target/match by that name.
Jan 18 12:40:09 Tardis /firewalld[1304]: ERROR: COMMAND_FAILED: '/sbin/iptables -w2 -t filter -C FORWARD -o docker0 -j DOCKER' failed: iptables: No chain/target/match by that name.
Jan 18 12:40:09 Tardis /firewalld[1304]: ERROR: COMMAND_FAILED: '/sbin/iptables -w2 -t filter -C FORWARD -j DOCKER-ISOLATION' failed: iptables: No chain/target/match by that name.
Jan 18 12:40:10 Tardis /firewalld[1304]: ERROR: COMMAND_FAILED: '/sbin/iptables -w2 -t nat -C POSTROUTING -s 172.17.0.0/16 ! -o docker0 -j MASQUERADE' failed: iptables: No chain/target/match by that name.
Jan 18 12:40:10 Tardis /firewalld[1304]: ERROR: COMMAND_FAILED: '/sbin/iptables -w2 -t nat -C DOCKER -i docker0 -j RETURN' failed: iptables: Bad rule (does a matching rule exist in that chain?).
Jan 18 12:40:10 Tardis /firewalld[1304]: ERROR: COMMAND_FAILED: '/sbin/iptables -w2 -D FORWARD -i docker0 -o docker0 -j DROP' failed: iptables: Bad rule (does a matching rule exist in that chain?).
Jan 18 12:40:10 Tardis /firewalld[1304]: ERROR: COMMAND_FAILED: '/sbin/iptables -w2 -t filter -C FORWARD -i docker0 -o docker0 -j ACCEPT' failed: iptables: Bad rule (does a matching rule exist in that chain?).
Jan 18 12:40:10 Tardis /firewalld[1304]: ERROR: COMMAND_FAILED: '/sbin/iptables -w2 -t filter -C FORWARD -i docker0 ! -o docker0 -j ACCEPT' failed: iptables: Bad rule (does a matching rule exist in that chain?).
Jan 18 12:40:10 Tardis /firewalld[1304]: ERROR: COMMAND_FAILED: '/sbin/iptables -w2 -t filter -C FORWARD -o docker0 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT' failed: iptables: Bad rule (does a matching rule exist in that chain?).
Jan 18 12:40:10 Tardis /firewalld[1304]: ERROR: COMMAND_FAILED: '/sbin/iptables -w2 -t filter -C FORWARD -o docker0 -j DOCKER' failed: iptables: No chain/target/match by that name.

```

---

