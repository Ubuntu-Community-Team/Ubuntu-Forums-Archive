---
title: "IP Tables Blocking a particular subnet"
date: 2020-06-10
forum: Networking &amp; Wireless
---

### Post by shatz84is on 2020-06-10
Dear All,

I want to access machine from a particular sub-net (say 10.0.0.0/24 to 10.2.0.1/24) . I am able to access all other machines in that particular sub-net  except this Ubuntu machine.
I disabled UFW and checked but no luck !

How I can overcome this issue by modifying the IPTables ;current IPTables as following. Is anything restricting here since am not an expert in IPTables. 

#iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy DROP)
target     prot opt source               destination
DOCKER-USER  all  --  anywhere             anywhere
DOCKER-ISOLATION-STAGE-1  all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain DOCKER (3 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             172.20.0.2           tcp dpt:24224
ACCEPT     tcp  --  anywhere             172.20.0.3           tcp dpt:5443
ACCEPT     tcp  --  anywhere             172.20.0.3           tcp dpt:5080
ACCEPT     tcp  --  anywhere             172.20.0.3           tcp dpt:81
ACCEPT     udp  --  anywhere             172.20.0.4           udp dpt:2056

Chain DOCKER-ISOLATION-STAGE-1 (1 references)
target     prot opt source               destination
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere
DROP       all  -- !172.19.0.0/16        anywhere
DROP       all  --  anywhere            !172.19.0.0/16
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere

Chain DOCKER-ISOLATION-STAGE-2 (3 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere
DROP       all  --  anywhere             anywhere
DROP       all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere

Chain DOCKER-USER (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere





Thanks & Regards,
Shatz

---

