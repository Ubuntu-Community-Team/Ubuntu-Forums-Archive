---
title: "Ubuntu 18.04 Server as router"
date: 2018-12-24
forum: Networking &amp; Wireless
---

### Post by pelgrim on 2018-12-24
I installed Ubuntu server (18.04) months ago which I would like to configure as a router, besides all the other stuff it's already doing for me.

In the older versions things worked fine, but it appears since 18.04 things are very different now.
I tried countless things I found, but with no result.
A few examples:
to the letter: [https://www.ascinc.com/blog/linux/how-to-build-a-simple-router-with-ubuntu-server-18-04-1-lts-bionic-beaver/](https://www.ascinc.com/blog/linux/how-to-build-a-simple-router-with-ubuntu-server-18-04-1-lts-bionic-beaver/)
read and tried: [https://help.ubuntu.com/lts/serverguide/firewall.html](https://help.ubuntu.com/lts/serverguide/firewall.html)
[https://linoxide.com/linux-how-to/install-configure-dhcp-ubuntu/](https://linoxide.com/linux-how-to/install-configure-dhcp-ubuntu/)
[http://manpages.ubuntu.com/manpages/bionic/man5/netplan.5.html](http://manpages.ubuntu.com/manpages/bionic/man5/netplan.5.html)

What do I have:
- A working Ubuntu Server 18.04 that is connected to internet, DHCP and UFW up and running
- A working Ubuntu Client 17.04 that can ping to the server (and the other way arround)
  I can temp. connect the client directly to internet, which is working and I use to search stuff,
  or I can connect my server and use a switch between my server and client, which enables me to test "whatever I found"

Of course, switching cables each time is time consuming and nerve wrecking.
In next post I will dig up the configuration files from my server and put them here.
If there is additional information I need to provide, I'm happy to hear it.

Thanks in advance if you can help me out.

---

### Post by pelgrim on 2018-12-24
**/etc/netplan/50-cloud-init.yaml**
```
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        enp5s0:
            dhcp4: true
        enp4s0:
            dhcp4: false
            dhcp6: false
            addresses:
             - 192.168.0.1/24
            gateway4: 192.168.0.1
            nameservers:
                addresses:
                - 192.168.0.1
                - 1.1.1.1
                - 1.0.0.1
                search: []
    version: 2

```
**/etc/ufw/sysctl.conf**```

# Configuration file for setting network variables. Please note these settings
# override /etc/sysctl.conf and /etc/sysctl.d. If you prefer to use
# /etc/sysctl.conf, please adjust IPT_SYSCTL in /etc/default/ufw. See
# Documentation/networking/ip-sysctl.txt in the kernel source code for more
# information.
#

# Uncomment this to allow this host to route packets between interfaces
net/ipv4/ip_forward=1
net/ipv4/conf/all/forwarding=1
net/ipv6/conf/default/forwarding=1
net/ipv6/conf/all/forwarding=1

# Disable ICMP redirects. ICMP redirects are rarely used but can be used in
# MITM (man-in-the-middle) attacks. Disabling ICMP may disrupt legitimate
# traffic to those sites.
net/ipv4/conf/all/accept_redirects=0
net/ipv4/conf/default/accept_redirects=0
net/ipv6/conf/all/accept_redirects=0
net/ipv6/conf/default/accept_redirects=0

# Ignore bogus ICMP errors
net/ipv4/icmp_echo_ignore_broadcasts=1
net/ipv4/icmp_ignore_bogus_error_responses=1
net/ipv4/icmp_echo_ignore_all=0

# Don't log Martian Packets (impossible addresses)
# packets
net/ipv4/conf/all/log_martians=0
net/ipv4/conf/default/log_martians=0

#net/ipv4/tcp_fin_timeout=30
#net/ipv4/tcp_keepalive_intvl=1800

# Uncomment this to turn off ipv6 autoconfiguration
#net/ipv6/conf/default/autoconf=1
#net/ipv6/conf/all/autoconf=1

# Uncomment this to enable ipv6 privacy addressing
#net/ipv6/conf/default/use_tempaddr=2
#net/ipv6/conf/all/use_tempaddr=2
```
**/etc/rc.local**
```
#!/bin/bash

# /etc/rc.local

# Default policy to drop all incoming packets.
iptables -P INPUT DROP
iptables -P FORWARD DROP

# Accept incoming packets from localhost and the LAN interface.
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i enp4so -j ACCEPT

# Accept incoming packets from the WAN if the router initiated the connection.
iptables -A INPUT -i enp5s0 -m conntrack \
--ctstate ESTABLISHED,RELATED -j ACCEPT

# Forward LAN packets to the WAN.
iptables -A FORWARD -i enp4s0 -o enp5s0 -j ACCEPT

# Forward WAN packets to the LAN if the LAN initiated the connection.
iptables -A FORWARD -i enp5s0 -o enp4s0 -m conntrack \
--ctstate ESTABLISHED,RELATED -j ACCEPT

# NAT traffic going out the WAN interface.
iptables -t nat -A POSTROUTING -o enp5s0 -j MASQUERADE

# rc.local needs to exit with 0
exit 0
```


**sudo ufw status**
```
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere                  
Samba                      ALLOW       192.168.0.0/24            
5432                       ALLOW       Anywhere                  
4848                       ALLOW       Anywhere                  
8080                       ALLOW       Anywhere                  
80                         ALLOW       Anywhere                  
Anywhere                   ALLOW       192.168.0.0/24            
192.168.0.0/24             ALLOW       Anywhere                  
22 (v6)                    ALLOW       Anywhere (v6)             
5432 (v6)                  ALLOW       Anywhere (v6)             
4848 (v6)                  ALLOW       Anywhere (v6)             
8080 (v6)                  ALLOW       Anywhere (v6)             
80 (v6)                    ALLOW       Anywhere (v6)
``` 


**server: ifconfig**
```
enp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.1  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 ...........................  prefixlen 64  scopeid 0x20<link>
        ether ..........................  txqueuelen 1000  (Ethernet)
        RX packets 63453  bytes 5418569 (5.4 MB)
        RX errors 0  dropped 200  overruns 0  frame 0
        TX packets 38940  bytes 9080716 (9.0 MB)
        TX errors 1  dropped 0 overruns 1  carrier 0  collisions 0

enp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet ???.???.???.???  netmask 255.255.248.0  broadcast ???.???.???.???
        inet6 ......................  prefixlen 64  scopeid 0x20<link>
        ether .....................  txqueuelen 1000  (Ethernet)
        RX packets 802886  bytes 48184897 (48.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 171  bytes 29795 (29.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 76794  bytes 35444867 (35.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 76794  bytes 35444867 (35.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

---

### Post by pelgrim on 2019-01-04
Nobody can help me with this one ?

---

### Post by pelgrim on 2019-01-04
After too many attempts, things are configured like described in this website, but with the same result:
[https://www.ascinc.com/blog/linux/how-to-build-a-simple-router-with-ubuntu-server-18-04-1-lts-bionic-beaver/](https://www.ascinc.com/blog/linux/how-to-build-a-simple-router-with-ubuntu-server-18-04-1-lts-bionic-beaver/)

Any help would be highly appreciated.

---

### Post by Doug S on 2019-01-04
I do not understand the enp5s0 configuration as listed in your "server: ifconfig" section, as it doesn't seem to have an IP address.

You are mixing UFW with additional direct iptabels rules. Could you list your entire resulting iptables rule set. Do: "sudo iptables -v -x -n -L" and "sudo iptables -t nat -v -x -n -L".

---

### Post by pelgrim on 2019-01-04
thank you for your help Doug S.
It must be something stupid or small, but just can't get my head around it. Missing the "good old times" when netplan was not a must-do ...
As for your remark: I deleted mac adresses and my IP address before putting it on the forum.
You're probably right I started mixing up the wrong things, I just don't have a clue anymore after following too many different websites and forums.

**sudo iptables -v -x -n -L**
```
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
   22922  1941278 ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   22922  1941278 ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     117    19923 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  enp4so *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  enp5s0 *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
   25699  1613270 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   25699  1613270 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   25699  1613270 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   25699  1613270 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   25699  1613270 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   25699  1613270 ufw-track-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  enp4s0 enp5s0  0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  enp5s0 enp4s0  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT 3 packets, 144 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
   46318  3965263 ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   46318  3965263 ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   11149   733111 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   11149   733111 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   11149   733111 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   11149   733111 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      64     6000 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
      42    10315 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:138
       0        0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:139
       0        0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:445
      11     3608 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:68
       0        0 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
   25699  1613270 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
   16903  1468274 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    5660   417832 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
       0        0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
       1       84 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
     358    55088 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            224.0.0.251          udp dpt:5353
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            239.255.255.250      udp dpt:1900
     358    55088 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
   30501  2713585 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    4668   518567 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
   11149   733111 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID limit: avg 3/min burst 10
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      44     6634 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
     314    48454 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
       0        0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
    pkts      bytes target     prot opt in     out     source               destination         
     117    19923 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
   19209  1152540 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
    6490   460730 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW

Chain ufw-track-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
    6275   376500 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
    4871   356467 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW

Chain ufw-user-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       6      360 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:22
     202    29527 ACCEPT     udp  --  *      *       192.168.0.0/24       0.0.0.0/0            multiport dports 137,138 /* 'dapp_Samba' */
       6      360 ACCEPT     tcp  --  *      *       192.168.0.0/24       0.0.0.0/0            multiport dports 139,445 /* 'dapp_Samba' */
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:5432
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:5432
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:4848
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:4848
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8080
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:8080
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:80
      27     4918 ACCEPT     all  --  *      *       192.168.0.0/24       0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            192.168.0.0/24      

Chain ufw-user-limit (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-input (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-output (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination
```

**sudo iptables -t nat -v -x -n -L**```

Chain PREROUTING (policy ACCEPT 7388 packets, 478892 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 59 packets, 7545 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 4423 packets, 286084 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 1138 packets, 74244 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 MASQUERADE  all  --  *      enp5s0  192.168.0.0/24       0.0.0.0/0           
      19     4469 MASQUERADE  all  --  *      enp5s0  0.0.0.0/0            0.0.0.0/0           
   10467   671321 MASQUERADE  all  --  *      enp4s0  0.0.0.0/0            0.0.0.0/0
```

---

### Post by slickymaster on 2019-01-04
@pelgrim:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output because when posted as plain text it loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of code tags makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by Doug S on 2019-01-04
> **pelgrim said:**
> **sudo iptables -t nat -v -x -n -L**```

Chain PREROUTING (policy ACCEPT 7388 packets, 478892 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 59 packets, 7545 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 4423 packets, 286084 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 1138 packets, 74244 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       [COLOR="#FF0000"]0        0 MASQUERADE  all  --  *      enp5s0  192.168.0.0/24       0.0.0.0/0 [/COLOR]          
      19     4469 MASQUERADE  all  --  *      enp5s0  0.0.0.0/0            0.0.0.0/0           
   [COLOR="#FF0000"]10467   671321 MASQUERADE  all  --  *      enp4s0  0.0.0.0/0            0.0.0.0/0[/COLOR]
```The rules in red above do not agree with what you wrote in earlier posts. Suggest you delete them. You do not want to MASQUERADE in the LAN direction, only in the WAN direction. What is the IP address of your 17.04 client?

---

### Post by pelgrim on 2019-01-04
ok, how do I do that ?

My configuration looks like what you find in here
[https://www.ascinc.com/blog/linux/how-to-build-a-simple-router-with-ubuntu-server-18-04-1-lts-bionic-beaver/](https://www.ascinc.com/blog/linux/how-to-build-a-simple-router-with-ubuntu-server-18-04-1-lts-bionic-beaver/)

The client (Ubuntu 18.04) has 192.168.0.3 when I use the dhcp option, when I configure manually 192.168.0.2

---

### Post by pelgrim on 2019-01-04
just to make sure, made some copies of the config files as they are now:

rc.local

```

#!/bin/bash

# /etc/rc.local

# Default policy to drop all incoming packets.
iptables -P INPUT DROP
iptables -P FORWARD DROP

# Accept incoming packets from localhost and the LAN interface.
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i enp4so -j ACCEPT

# Accept incoming packets from the WAN if the router initiated the connection.
iptables -A INPUT -i enp5s0 -m conntrack \
--ctstate ESTABLISHED,RELATED -j ACCEPT

# Forward LAN packets to the WAN.
iptables -A FORWARD -i enp4s0 -o enp5s0 -j ACCEPT

# Forward WAN packets to the LAN if the LAN initiated the connection.
iptables -A FORWARD -i enp5s0 -o enp4s0 -m conntrack \
--ctstate ESTABLISHED,RELATED -j ACCEPT

# NAT traffic going out the WAN interface.
iptables -t nat -A POSTROUTING -o enp5s0 -j MASQUERADE

# rc.local needs to exit with 0
exit 0

```

relevant part of dhcpd.conf

```

# dhcpd.conf
#
# Sample configuration file for ISC dhcpd
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#

# option definitions common to all supported networks...
option domain-name "pelgrim";
option domain-name-servers 195.130.130.5, 195.130.131.5;

default-lease-time 600;
max-lease-time 7200;

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# A slightly different configuration for an internal subnet.
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.1 192.168.0.24;
  option routers 192.168.0.1;
  option subnet-mask 255.255.255.0;
  option broadcast-address 192.168.0.255;
}

```

/etc/netplan/50-cloud-init.yaml

```

network:
    ethernets:
        enp5s0:
            dhcp4: true
        enp4s0:
            dhcp4: false
            addresses:
             - 192.168.0.1/24
            gateway4: 192.168.0.1
            nameservers:
                addresses:
                - 195.130.130.5
                - 195.130.131.5
                search: [telenet.be]
    version: 2

```

/etc/ufw/before.rules

```


#
# rules.before
#
# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]
# Forward traffic from eth1 through eth0.
-A POSTROUTING -s 192.168.0.0/24 -o enp5s0 -j MASQUERADE
# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

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

*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines

# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT

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

# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT


```

I tried just now to disactivate this line in /etc/ufw/before.rules
-A POSTROUTING -s 192.168.0.0/24 -o enp5s0 -j MASQUERADE
and performed this:
sudo ufw disable && sudo ufw enable

but with no success, so I activated that line again.

---

### Post by Doug S on 2019-01-04
> **pelgrim said:**
> I tried just now to disactivate this line in /etc/ufw/before.rules
-A POSTROUTING -s 192.168.0.0/24 -o enp5s0 -j MASQUERADE
and performed this:
sudo ufw disable && sudo ufw enable

but with no success, so I activated that line again.O.K., but that isn't the line that breaks things, it is the other line that i had in [COLOR="#FF0000"]red[/COLOR] before (at least, I think) . Although I don't know why that path isn't being taken at all (which is why I asked for the ip address of the other computer) , and it seems to fall to the next  MASQUERADE line.

---

### Post by pelgrim on 2019-01-04
No idea what to do now.
These 2 lines in red are only the result of that command ...

**sudo iptables -t nat -v -x -n -L**```

Chain PREROUTING (policy ACCEPT 7388 packets, 478892 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 59 packets, 7545 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 4423 packets, 286084 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 1138 packets, 74244 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
[COLOR="#FF0000"]       0        0 MASQUERADE  all  --  *      enp5s0  192.168.0.0/24       0.0.0.0/0 [/COLOR]          
      19     4469 MASQUERADE  all  --  *      enp5s0  0.0.0.0/0            0.0.0.0/0           
[COLOR="#FF0000"]   10467   671321 MASQUERADE  all  --  *      enp4s0  0.0.0.0/0            0.0.0.0/0[/COLOR]
```

---

### Post by Doug S on 2019-01-04
> **pelgrim said:**
> No idea what to do now.
I don't use UFW, and do not like it. I would get rid of it entirely, and do everything in iptables.
You can also use tcpdump (or wireshark, if you prefer) to attempt to trace where things go astray.
You can also use the packet counters to attempt to observe where things go astray.
Additionally, and for testing/debugging, extra logging rules can be added to iptables to gain insight into what packets take which path.

> **pelgrim said:**
> These 2 lines in red are only the result of that command ...

**sudo iptables -t nat -v -x -n -L**```

Chain PREROUTING (policy ACCEPT 7388 packets, 478892 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 59 packets, 7545 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 4423 packets, 286084 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 1138 packets, 74244 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
[COLOR="#FF0000"]       0        0 MASQUERADE  all  --  *      enp5s0  192.168.0.0/24       0.0.0.0/0 [/COLOR]          
      19     4469 MASQUERADE  all  --  *      enp5s0  0.0.0.0/0            0.0.0.0/0           
[COLOR="#FF0000"]   10467   671321 MASQUERADE  all  --  *      enp4s0  0.0.0.0/0            0.0.0.0/0[/COLOR]
```well, for a test delete the 3rd rule:
```
sudo iptables -t nat -D POSTROUTING 3
```I think I have the syntax correct, not tested.

---

### Post by pelgrim on 2019-01-05
I'm completely lost now.
3rd rule ?
Of what file ?
I rather fix things in the config files and restart services, or reboot if I don't know how.

Anyway, I didn't test my WAN connection on the server yesterday, I noticed this morning I can not ping out anymore,
although I do get an IP from my internet provider.

Now I'm starting to get desperate, at least the last half year I got my server up and running,
this routing was a huge discomfort for when I was at home (not that much), but at least only a discomfort.
Priorities are simple
1. Server online
that's it.

---

### Post by pelgrim on 2019-01-05
so, an update to tell whatever I tried, I can't get my server back online,
all that works is the LAN network.
I need to get my server back online today, leaving tomorrow ...

---

### Post by pelgrim on 2019-01-05
Next chapter in the saga:

when I do this:
/etc/netplan/50-cloud-init.yaml
```

network:
    ethernets:
        enp5s0:
            dhcp4: true
    version: 2
```

I get only WAN to work (server is back on internet), but no LAN connection.

But when I do variations of this:

```

network:
    ethernets:
        enp5s0:
            dhcp4: true
        enp4s0:
            dhcp4: false
            addresses:
             - 192.168.0.1/24
            gateway4: 192.168.0.1
            nameservers:
                addresses:
                - 192.168.0.1
                search: []
    version: 2
```

I get only LAN to work, no WAN connection on my server.

---

### Post by pelgrim on 2019-01-05
and here it finally is, the solution:

/etc/netplan/50-cloud-init.yaml

```

network:
    ethernets:
        enp5s0:
            dhcp4: true
        enp4s0:
            dhcp4: false
            addresses:
             - 192.168.0.1/24
            gateway4: 192.168.0.1
    version: 2
```

This contradicts any article I found in the last half year about this subject, every single one of them specifies nameservers.
Would be very interesting to know how and why this works ...

---

### Post by Doug S on 2019-01-05
> **pelgrim said:**
> I'm completely lost now.
3rd rule ?
Of what file ?Of the resulting iptables rule set. I do not know which file, since I don't know where the rule came from.
> **pelgrim said:**
> I rather fix things in the config files and restart services, or reboot if I don't know how.Me too. The suggestion to delete the rule manually was to determine if we were on the right track or not.

> **pelgrim said:**
> and here it finally is, the solution:

...[snip]...

This contradicts any article I found in the last half year about this subject, every single one of them specifies nameservers.
Would be very interesting to know how and why this works ...So would I. Would you post the outputs for "sudo iptables -v -x -n -L" and "sudo iptables -t nat -v -x -n -L" for those netplan configurations?

---

### Post by pelgrim on 2019-01-05
gladly

sudo iptables -v -x -n -L

```

Chain INPUT (policy DROP 122 packets, 6348 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
   68890 82577525 ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   68890 82577525 ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     406    30492 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     343    19811 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     343    19811 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     343    19811 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      16     1208 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  enp4so *       0.0.0.0/0            0.0.0.0/0           
       1     1136 ACCEPT     all  --  enp5s0 *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
  158446 108398812 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  158446 108398812 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    2270   169149 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    2270   169149 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    2270   169149 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    2270   169149 ufw-track-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      47     4595 ACCEPT     all  --  enp4s0 enp5s0  0.0.0.0/0            0.0.0.0/0           
      24     1940 ACCEPT     all  --  enp5s0 enp4s0  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
   44449 10381254 ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   44449 10381254 ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     336    33347 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     336    33347 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     336    33347 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     336    33347 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
       4     1014 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:138
       0        0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:139
       0        0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:445
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:68
       0        0 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      76     3920 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
   97791 82188609 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
     585    37933 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
     311    27868 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    1913   281980 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
       0        0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
       1       84 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
       2      916 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
     191    14328 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            224.0.0.251          udp dpt:5353
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            239.255.255.250      udp dpt:1900
     191    14328 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
     311    27868 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    1661   483036 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
      54     4798 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID limit: avg 3/min burst 10
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
     176    11404 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
      15     2924 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
       0        0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
    pkts      bytes target     prot opt in     out     source               destination         
       4     1014 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
     275    16500 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
     310    21433 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW

Chain ufw-track-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      28     1680 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
      26     3118 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW

Chain ufw-user-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       4      204 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:22
      21     2810 ACCEPT     udp  --  *      *       192.168.0.0/24       0.0.0.0/0            multiport dports 137,138 /* 'dapp_Samba' */
       0        0 ACCEPT     tcp  --  *      *       192.168.0.0/24       0.0.0.0/0            multiport dports 139,445 /* 'dapp_Samba' */
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:5432
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:5432
      14      840 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:4848
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:4848
       9      524 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8080
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:8080
      11      620 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:80
       6     1968 ACCEPT     all  --  *      *       192.168.0.0/24       0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            192.168.0.0/24      
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80

Chain ufw-user-limit (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-input (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-output (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination
```


sudo iptables -t nat -v -x -n -L

```

Chain PREROUTING (policy ACCEPT 778 packets, 51411 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 53 packets, 5666 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 128 packets, 9395 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 81 packets, 5881 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
    2264   149745 MASQUERADE  all  --  *      enp5s0  0.0.0.0/0            0.0.0.0/0 
```

---

### Post by pelgrim on 2019-01-05
o yeah, forgot, now that I got my network running "smootly", glassfish can't start anymore.
And nope, didn't change a single bit in there ...
But that's for another kind of forum if I don't find anything.

---

### Post by Doug S on 2019-01-06
> **pelgrim said:**
> sudo iptables -t nat -v -x -n -L

```

Chain PREROUTING (policy ACCEPT 778 packets, 51411 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 53 packets, 5666 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 128 packets, 9395 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 81 packets, 5881 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
    2264   149745 MASQUERADE  all  --  *      enp5s0  0.0.0.0/0            0.0.0.0/0 
```That is really interesting. Now the POSTROUTING rules are as expected. And the only chnage was to the "/etc/netplan/50-cloud-init.yaml" file?

---

