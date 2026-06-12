---
title: "Port Forwarding, Virtualizaiton"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by kamil.choudhury on 2008-06-23
I've been banging my head on the wall about this one for a while now, so I thought I'd give the forum a shot. 

I want to forward port 25 from the outside world (eth0) to nyx. 

Salient points for the network (pictured below): 

[list]
[*] **nyx** is a virtualized Win2k3 instance bound to eth1, which is plugged into a switch. 
[*] **ganieda** and **gwenhyvyar** are wired clients, plugged into eth2 through the same switch as eth1. 
[*] **salrana** is a wireless client, tapping into the 192.168.0 subnet via bridge br0. 
[*] IP Addresses, names for everyone:
[list]
[*] eth0: serenity.domain.net, assigned by ISP through DHCP
[*] eth1: serenity2.domain.local, 192.168.1.1
[list]
[*] **nyx**: nyx.domain.local, 192.168.1.11[/list]
[*] br0 (bridge of eth1, ath0): serenity.domain.local, 192.168.0.1[list]
[*] **ganieda**: ganieda.domain.local, 192.168.0.21
[*] **gwenhyvyar**: gwenhyvyar.domain.local, 192.168.0.22
[*] **salrana**: salrana.domain.local, 192.168.0.61[/list][/list]
[*] eth1 and eth2 are plugged into the same switch, which has an IP address of 192.168.0.2. 
[*] Output of sudo route: 
```

192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 br0
[isp ip]        *               255.255.248.0   U     0      0        0 eth0
default         [serenity.domain.net]           UG    0      0        0 eth0

```
[*] My /etc/network/interfaces file: 
```

# The loopback network interface
auto lo
iface lo inet loopback

# Configure eth0
auto eth0
iface eth0 inet dhcp

# Configure eth1
auto eth1
iface eth1 inet static
        address 192.168.1.1
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255

# Configure ath0
auto ath0
iface ath0 inet manual
        pre-up wlanconfig ath0 destroy
        pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap bssid
        wireless-mode master
# Configure br0
auto br0
iface br0 inet static
        address 192.168.0.1
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        bridge_ports eth2 ath0

```
[*] My firewall script: 
```

#!/bin/bash

#########
# Aliases
#########

# Binaries
IPTABLES="/sbin/iptables"
MODPROBE="/sbin/modprobe"

# Interfaces
LAN_IF="br0"
WAN_IF="eth0"

# IP Addresses for
# ... interfaces:
INT_IP="192.168.0.0/24"
WAN_IP="`/sbin/ifconfig $WAN_IF | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"

# ... servers:
NYX="192.168.1.11"

#####################
# Initialize iptables
#####################

# Load NAT modules
$MODPROBE ipt_MASQUERADE

# Enable routing ability
echo 1 > /proc/sys/net/ipv4/ip_forward

# Flush all tables
$IPTABLES -F

###############
# Define chains
###############

##### Port Forwarding #####
# For incoming SMTP packets, rewrite destination and release
$IPTABLES -t nat    -A PREROUTING  -p tcp -i $WAN_IF -d $WAN_IP --dport 25   -j DNAT    --to-destination $NYX:25
$IPTABLES -t filter -A FORWARD     -p tcp -i $WAN_IF -d $NYX    --dport 25   -j ACCEPT

##### Other NAT ###########
# For outgoing packets, rewrite source and release if correct in state
$IPTABLES -t nat    -A POSTROUTING -o $WAN_IF                                     -j MASQUERADE
$IPTABLES -t filter -A FORWARD     -m state --state ESTABLISHED,RELATED           -j ACCEPT

```
[*] A rough diagram of my network: 
```
 
       +-------------------------------+
       |                               |
       |                             +----+     +---+   +-----+
     +----+                          |eth1|-----| s |---| nyx | <- - - - - 192.168.1.11
-----|eth0|  serenity                +----+     |   |   +-----+
     +----+                            |        | w |
       |                  +----+       |        |   |<- - - - - - - - - - -192.168.0.2
       |                  |eth2|--+    |        | i |
       |                  +----+  |  +----+     |   |   +---------+
       |                          +--|br0 |--+--| t |---| ganieda | <- - - 192.168.0.21
       |                  +----+  |  +----+  |  |   |   +---------+
       |                  |ath0|--+    |     |  | c |
       |                  +----+       |     |  |   |   +------------+
       +-------------------------------+     |  | h |---| gwenhyvyar | <- -192.168.0.22
                                             |  +---+   +------------+
                                             |
                                             |
                                          wireless
                                             |          +---------+
                                             +----------| salrana | <- - - 192.168.0.61
                                                        +---------+

```[/list]


Everyone can ping everyone else from inside the network, and I can telnet into the SMTP server running on nyx from ganieda or gwenhyvyar. When I try to do the same from an outside server, though, I get a "cannot find route to host". I'm assuming that there's something wrong with my forwarding/firewall script. Anyone have any idea what it is? Is this situation -- two subnets going through one switch -- even tenable? 

Thanks in advance for any assistance at all. If you need further clarification, I can post more information.

---

### Post by kamil.choudhury on 2008-06-23
.

---

