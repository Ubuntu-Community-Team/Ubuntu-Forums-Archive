---
title: "Ufw &amp; nat"
date: 2016-05-06
forum: Networking &amp; Wireless
---

### Post by jean-baptiste2 on 2016-05-06
Hello everybody,


I will expose you my problem with my server DHCP & FW (with iptables/ufw).


I have two network, one who I have my internet acces on 192.168.1.1 (my DNS) and another private network with my DHCP server on 10.10.10.0/24. My host is connect on the two network.

I have great configure my DHCP server who give dynamic address on my private network with for DNS 192.168.1.1.
On this host I have configure my NAT acces trought ufw to have an internet access on my internet nework. But I will control my flux between my private network and internet.


What I have do:


/etc/default/ufw
```
DEFAULT_FORWARD_POLICY="ACCEPT"
```


/etc/ufw/sysctl.conf
```
net/ipv4/ip_forward=1
net/ipv6/conf/default/forwarding=1
net/ipv6/conf/all/forwarding=1
```


/etc/ufw/before.rules
```

#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#


# règles pour la table NAT
*nat


:POSTROUTING ACCEPT [0:0]


# transmission du trafic provenant de enp0s3 vers enp0s8


-A POSTROUTING -s 10.10.10.0/24 -o enp0s8 -j MASQUERADE


COMMIT


# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines




# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT


# quickly process packets for which we already have a connection
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-forward -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT


# drop INVALID packets (logs these in loglevel medium and higher)
-A ufw-before-input -m conntrack --ctstate INVALID -j ufw-logging-deny
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP


# ok icmp codes for INPUT
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT


# ok icmp code for FORWARD
-A ufw-before-forward -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type echo-request -j ACCEPT




# allow dhcp client to work
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT


#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local


# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN


# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN


# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN


# all other non-local packets are dropped
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP


# allow MULTICAST mDNS for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT


# allow MULTICAST UPnP for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT


#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local


# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN


# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN


# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN


# all other non-local packets are dropped
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP


# allow MULTICAST mDNS for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT


# allow MULTICAST UPnP for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT


# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

```


Then I active my rules:


```
sudo ufw default deny incoming
``` & ```
sudo ufw default deny outgoing]
``` & ```
sudo ufw allow ssh
```

Ok, It's perfect ! My host doesn't any more access to internet but the SSH working. However... my Nat is working great, a little too well, because any rules of my ufw is applicated on my NAT. All my internal client can access to internet without passing by the ufw filter. In this exemple my host doesn't have the access to internet (it's my rules) but all my clients yes... If I turn off UFW and reboot my host, my clients doesn't anymore access to internet (logic because UFW is off) and my host access to internet. I turn UFW again, my host can't go to internet (normal) but my clients can again go internet....

Why and where is my mistake ? What have I wrong with my UFW rules or configuration ?


A little sudo iptables -L to help:


```
administrateur@DHCP:~$ sudo iptables -L
[sudo] password for administrateur:
Chain INPUT (policy DROP)
target     prot opt source               destination
ufw-before-logging-input  all  --  anywhere             anywhere
ufw-before-input  all  --  anywhere             anywhere
ufw-after-input  all  --  anywhere             anywhere
ufw-after-logging-input  all  --  anywhere             anywhere
ufw-reject-input  all  --  anywhere             anywhere
ufw-track-input  all  --  anywhere             anywhere
 
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ufw-before-logging-forward  all  --  anywhere             anywhere
ufw-before-forward  all  --  anywhere             anywhere
ufw-after-forward  all  --  anywhere             anywhere
ufw-after-logging-forward  all  --  anywhere             anywhere
ufw-reject-forward  all  --  anywhere             anywhere
ufw-track-forward  all  --  anywhere             anywhere
 
Chain OUTPUT (policy DROP)
target     prot opt source               destination
ufw-before-logging-output  all  --  anywhere             anywhere
ufw-before-output  all  --  anywhere             anywhere
ufw-after-output  all  --  anywhere             anywhere
ufw-after-logging-output  all  --  anywhere             anywhere
ufw-reject-output  all  --  anywhere             anywhere
ufw-track-output  all  --  anywhere             anywhere
 
Chain ufw-after-forward (1 references)
target     prot opt source               destination
 
Chain ufw-after-input (1 references)
target     prot opt source               destination
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
 
Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination
 
Chain ufw-after-logging-input (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "
 
Chain ufw-after-logging-output (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "
 
Chain ufw-after-output (1 references)
target     prot opt source               destination
 
Chain ufw-before-forward (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ufw-user-forward  all  --  anywhere             anywhere
 
Chain ufw-before-input (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             ctstate INVALID
DROP       all  --  anywhere             anywhere             ctstate INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere
 
Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination
 
Chain ufw-before-logging-input (1 references)
target     prot opt source               destination
 
Chain ufw-before-logging-output (1 references)
target     prot opt source               destination
 
Chain ufw-before-output (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere
 
Chain ufw-logging-allow (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "
 
Chain ufw-logging-deny (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "
 
Chain ufw-not-local (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere
 
Chain ufw-reject-forward (1 references)
target     prot opt source               destination
 
Chain ufw-reject-input (1 references)
target     prot opt source               destination
 
Chain ufw-reject-output (1 references)
target     prot opt source               destination
 
Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
 
Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere
 
Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere
 
Chain ufw-track-forward (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW
 
Chain ufw-track-input (1 references)
target     prot opt source               destination
 
Chain ufw-track-output (1 references)
target     prot opt source               destination
 
Chain ufw-user-forward (1 references)
target     prot opt source               destination
 
Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     udp  --  anywhere             anywhere             udp dpt:ssh
 
Chain ufw-user-limit (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
 
Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
 
Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination
 
Chain ufw-user-logging-input (0 references)
target     prot opt source               destination
 
Chain ufw-user-logging-output (0 references)
target     prot opt source               destination
 
Chain ufw-user-output (1 references)
target     prot opt source               destination
```




Thanks a lot at all in advance !!!


Jean-Baptiste

---

