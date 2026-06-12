---
title: "Docker + Ubuntu Server 22.04 + UFW networking issue"
date: 2022-09-01
forum: Networking &amp; Wireless
---

### Post by clayesson on 2022-09-01
[COLOR=#232629][FONT=-apple-system]I'm running a couple of docker containers on an Ubuntu server. Some of the containers expose ports on the host network. After a server reboot, all connections to the ports from outside the host are denied. This happens even if ufw is disabled. The solution I have found is to first enable and then disable ufw. This needs to be done after each boot... I've tried to completely uninstall ufw but the problem still exists. The only way I found to get it working again after uninstalling ufw was to reinstall ufw and toggle the ufw enabled/disabled.

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I have also tried the steps from here: [https://github.com/chaifeng/ufw-docker](https://github.com/chaifeng/ufw-docker), but the issue still remains. After opening the ports, everything works as expected, but as soon as the server is rebooted, all connections are refused. The problem is fixed by first disabling ufw and then enabling ufw.

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I suspect that some rules are missing when the server starts. After a ufw status toggle the rules are added correctly.

Any suggestions?

Iptables after a reboot. (No access to docker containers)
[/FONT][/COLOR]```

# Warning: iptables-legacy tables present, use iptables-legacy to see them
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain FORWARD (policy DROP 24 packets, 1472 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 271K  487M DOCKER-USER  all  --  any    any     anywhere             anywhere            
 271K  487M DOCKER-ISOLATION-STAGE-1  all  --  any    any     anywhere             anywhere            
 209K  332M ACCEPT     all  --  any    docker0  anywhere             anywhere             ctstate RELATED,ESTABLISHED
  328  101K DOCKER     all  --  any    docker0  anywhere             anywhere            
61591  155M ACCEPT     all  --  docker0 !docker0  anywhere             anywhere            
  304 99992 ACCEPT     all  --  docker0 docker0  anywhere             anywhere            


Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain DOCKER (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain DOCKER-ISOLATION-STAGE-1 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
61591  155M DOCKER-ISOLATION-STAGE-2  all  --  docker0 !docker0  anywhere             anywhere            
 271K  487M RETURN     all  --  any    any     anywhere             anywhere            


Chain DOCKER-ISOLATION-STAGE-2 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  any    docker0  anywhere             anywhere            
61591  155M RETURN     all  --  any    any     anywhere             anywhere            


Chain DOCKER-USER (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 271K  487M RETURN     all  --  any    any     anywhere             anywhere 

```[COLOR=#232629][FONT=-apple-system]

Iptables after UFW toggle enable/disable. (Working as expected).

[/FONT][/COLOR]```

# Warning: iptables-legacy tables present, use iptables-legacy to see them
Chain INPUT (policy ACCEPT 19 packets, 1320 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   57  3902 ufw-before-logging-input  all  --  any    any     anywhere             anywhere            
   57  3902 ufw-before-input  all  --  any    any     anywhere             anywhere            
   19  1320 ufw-after-input  all  --  any    any     anywhere             anywhere            
   19  1320 ufw-after-logging-input  all  --  any    any     anywhere             anywhere            
   19  1320 ufw-reject-input  all  --  any    any     anywhere             anywhere            
   19  1320 ufw-track-input  all  --  any    any     anywhere             anywhere            


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 595K 1037M DOCKER-USER  all  --  any    any     anywhere             anywhere            
 595K 1037M DOCKER-ISOLATION-STAGE-1  all  --  any    any     anywhere             anywhere            
 429K  725M ACCEPT     all  --  any    docker0  anywhere             anywhere             ctstate RELATED,ESTABLISHED
  356  104K DOCKER     all  --  any    docker0  anywhere             anywhere            
 165K  312M ACCEPT     all  --  docker0 !docker0  anywhere             anywhere            
  320  102K ACCEPT     all  --  docker0 docker0  anywhere             anywhere            
    1    48 ufw-before-logging-forward  all  --  any    any     anywhere             anywhere            
    1    48 ufw-before-forward  all  --  any    any     anywhere             anywhere            
    1    48 ufw-after-forward  all  --  any    any     anywhere             anywhere            
    1    48 ufw-after-logging-forward  all  --  any    any     anywhere             anywhere            
    1    48 ufw-reject-forward  all  --  any    any     anywhere             anywhere            
    1    48 ufw-track-forward  all  --  any    any     anywhere             anywhere            


Chain OUTPUT (policy ACCEPT 12 packets, 1420 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   36  3604 ufw-before-logging-output  all  --  any    any     anywhere             anywhere            
   36  3604 ufw-before-output  all  --  any    any     anywhere             anywhere            
   13  1588 ufw-after-output  all  --  any    any     anywhere             anywhere            
   13  1588 ufw-after-logging-output  all  --  any    any     anywhere             anywhere            
   13  1588 ufw-reject-output  all  --  any    any     anywhere             anywhere            
   13  1588 ufw-track-output  all  --  any    any     anywhere             anywhere            


Chain DOCKER (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain DOCKER-ISOLATION-STAGE-1 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 165K  312M DOCKER-ISOLATION-STAGE-2  all  --  docker0 !docker0  anywhere             anywhere            
 595K 1037M RETURN     all  --  any    any     anywhere             anywhere            


Chain DOCKER-ISOLATION-STAGE-2 (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  any    docker0  anywhere             anywhere            
 165K  312M RETURN     all  --  any    any     anywhere             anywhere            


Chain DOCKER-USER (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   49 15509 ufw-user-forward  all  --  any    any     anywhere             anywhere            
   13  3877 RETURN     all  --  any    any     10.0.0.0/8           anywhere            
   25  4181 RETURN     all  --  any    any     172.16.0.0/12        anywhere            
    0     0 RETURN     all  --  any    any     192.168.0.0/16       anywhere            
    0     0 RETURN     udp  --  any    any     anywhere             anywhere             udp spt:domain dpts:1024:65535
    0     0 ufw-docker-logging-deny  tcp  --  any    any     anywhere             192.168.0.0/16       tcp flags:FIN,SYN,RST,ACK/SYN
    0     0 ufw-docker-logging-deny  tcp  --  any    any     anywhere             10.0.0.0/8           tcp flags:FIN,SYN,RST,ACK/SYN
    0     0 ufw-docker-logging-deny  tcp  --  any    any     anywhere             172.16.0.0/12        tcp flags:FIN,SYN,RST,ACK/SYN
    0     0 ufw-docker-logging-deny  udp  --  any    any     anywhere             192.168.0.0/16       udp dpts:0:32767
    0     0 ufw-docker-logging-deny  udp  --  any    any     anywhere             10.0.0.0/8           udp dpts:0:32767
    0     0 ufw-docker-logging-deny  udp  --  any    any     anywhere             172.16.0.0/12        udp dpts:0:32767
   11  7451 RETURN     all  --  any    any     anywhere             anywhere            


Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-docker-logging-deny (6 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW DOCKER BLOCK] "
    0     0 DROP       all  --  any    any     anywhere             anywhere            


Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-track-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination 

```[COLOR=#232629][FONT=-apple-system]
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR]

---

